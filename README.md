[TOC]

# RabbitMQ in .NET

## Install RabbitMQ locally

Install RabbitMQ via [Rabbit docker images](https://hub.docker.com/_/rabbitmq) through [podman](https://podman.io/getting-started/installation) command:

```bash
podman run -d --hostname my-rabbit --name local-rabbit -p 15672:15672 -p 5672:5672 rabbitmq:3-management
```

Check logs:
```bash
podman logs -f local-rabbit
```

Access RabbitMQ dashboard <http://localhost:15672/> with default username / password `guest/guest`.


## Producer

Add below NuGet packages:
- `RabbitMQ.Client`
- `Newtonsoft.Json` used to serialize object to JSON string (bytes)

The producer connect to `amqp://guest:guest@localhost:5672`, and publish messages to `demo-queue` message queue repeatly. 


## Consumer

Add below NuGet packages:
- `RabbitMQ.Client`

The consumer connect to `amqp://guest:guest@localhost:5672`, and consume messages from `demo-queue` message queue and print the received message to the console. 

The consumer code: [MQConsumer](https://github.com/xdevops-caj-dotnet/MQConsumer).

## Testing
Launch consumer:
```bash
# run in the consumer *.csproj root folder
dotnet run
```

Launch producer:
```bash
# run in the producer *.csproj root folder in another terminal
dotnet run
```

Check the logs of the consumer and producer.
Check the "Queue" details in RabbitMQ dashboard.

## References
- [RabbitMQ in .Net Core](https://dotnetcorecentral.com/blog/rabbitmq-in-net-core/)

## More RabbitMQ examples
- [RabbitMQ Tutorials](https://www.rabbitmq.com/getstarted.html)