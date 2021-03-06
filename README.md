# Demo Kafka

A simple Docker compose for starting Kafka and export its metrics to display on Grafana.

Start

```sh
docker compose up -d
```

## Kafka

### Create a topic

```sh
docker compose exec kafka bash

kafka-topics.sh --bootstrap-server localhost:9092 --create \
    --topic demo \
    --partitions 3 \
    --replication-factor 1
```

### Listing topics

```sh
docker compose exec kafka bash

kafka-topics.sh --bootstrap-server localhost:9092 --list
```

### Produce Messages

```sh
docker compose exec kafka bash

kafka-console-producer.sh --bootstrap-server localhost:9092 --topic demo
```

### Consume Messages

```sh
docker compose exec kafka bash

kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic demo --from-beginning
```

## Exporter

### Restart

```sh
docker compose restart kafka_exporter
```

## Grafana

open [http://localhost:3000](http://localhost:3000) on your browser

login with
user: admin
pass: admin

### Add datasource

1. Click cog icon on the left sidebar
2. Select Prometheus
3. For URL input type `http://prometheus:9090`
4. Click Save & test button
