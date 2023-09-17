### Run the kafka server
1. kafka-storage.sh random-uuid
2. kafka-storage.sh format -t <uuid> -c <kafka-path>/config/kraft/server.properties
3. kafka-server-start.sh <kafka-path>/config/kraft/server.properties

### To create a topic in kafka and view the all topics
+ kafka-topics.sh --bootstrap-server localhost:9092 --topic demo_java --create --partitions 3 --replication-factor 1
+ kafka-topics.sh --bootstrap-server localhost:9092 --list
+ kafka-topics.sh --bootstrap-server localhost:9092 --topic demo_java --describe

### To produce message
+ kafka-console-producer.sh --bootstrap-server localhost:9092 --topic demo_java
+ kafka-console-producer.sh --bootstrap-server localhost:9092 --topic demo_java --property parse.key=true --property key.separator=:

### To consume message
+ kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic demo_java
+ kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic demo_java --from-beginning
+ kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic demo_java --formatter kafka.tools.DefaultMessageFormatter --property print.timestamp=true --property print.key=true --property print.value=true --property print.partition=true --from-beginning
+ kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic demo_java --group my-first-application
+ kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic demo_java --group my-second-application --from-beginning
+ kafka-consumer-groups.sh --bootstrap-server localhost:9092 --list
+ kafka-consumer-groups.sh --bootstrap-server localhost:9092 --describe --group my-second-application
+ kafka-consumer-groups.sh --bootstrap-server localhost:9092 --group my-first-application --reset-offsets --to-earliest --topic demo_java --dry-run
+ kafka-consumer-groups.sh --bootstrap-server localhost:9092 --group my-first-application --reset-offsets --to-earliest --topic demo_java --execute
