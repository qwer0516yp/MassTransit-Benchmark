# MassTransit Benchmark

A set of benchmarks for measuring the performance of MassTransit with the supported transports.


## Message Latency 

Measures the throughput (send, consume) and latency (time from send to receive) of messages. The number of clients can be scaled to simulate multiple concurrent messages being written to the queue, and the concurrency, prefetch counts, and other settings can also be adjusted.

## Usage


To see the usage, enter:

`dotnet run -f netcoreapp3.1 -c Release -- -?`

That will show all the details of using the benchmark.

## InMemory

`dotnet run -c Release -t --inmemory -- --count=100000 --prefetch=10 --clients=10`

### Output

```
Transport: InMemory
Operating System: Microsoft Windows NT 10.0.22631.0
Processor Count: 24
MassTransit Version: 7.2.0.0
Transport Concurrency Limit: 24
Running Message Latency Benchmark
Message Count: 100000
Clients: 10
Durable: False
Payload Length: 0
Prefetch Count: 10
Concurrency Limit: 0
Total send duration: 0:00:03.531887
Send message rate: 28313.48 (msg/s)
Total consume duration: 0:00:03.63517
Consume message rate: 27509.03 (msg/s)
Concurrent Consumer Count: 13
Avg Ack Time: 0ms
Min Ack Time: 0ms
Max Ack Time: 0ms
Med Ack Time: 0ms
95t Ack Time: 0ms
Avg Consume Time: 870ms
Min Consume Time: 57ms
Max Consume Time: 2125ms
Med Consume Time: 704ms
95t Consume Time: 2050ms

   57ms ************************************************************ (  31621)
  264ms ****************                                             (   8899)
  471ms ***************                                              (   8220)
  677ms **************                                               (   7545)
  884ms **************************                                   (  13742)
 1505ms *****************                                            (   9185)
 1711ms *****************                                            (   9019)
 1918ms **********************                                       (  11768)
Transport Concurrency Limit: 24
Running Request Response Benchmark
Message Count: 100000
Clients: 10
Durable: False
Prefetch Count: 10
Concurrency Limit: 0
Total consume duration: 0:00:10.9943656
Consume message rate: 9095.57 (msg/s)
Total request duration: 0:00:10.9943903
Request rate: 9095.55 (msg/s)
Concurrent Consumer Count: 13
Avg Request Time: 1ms
Min Request Time: 0ms
Max Request Time: 1365ms
Med Request Time: 0ms
95t Request Time: 1ms
Avg Consume Time: 1ms
Min Consume Time: -5ms
Max Consume Time: 1354ms
Med Consume Time: 0ms
95t Consume Time: 0ms

Request duration distribution
    0ms ************************************************************ (  99887)
  273ms                                                              (     17)
  409ms                                                              (     26)
  546ms                                                              (      8)
  682ms                                                              (     35)
  819ms                                                              (     18)
 1229ms                                                              (      8)
```

## RabbitMQ

A good example that really hits RabbitMQ pretty hard.

`dotnet run -f netcoreapp3.1 -c Release -- --count=100000 --prefetch=1000 --clients=100`

### Output

```
MassTransit Benchmark

Transport: RabbitMQ
Host: localhost
Virtual Host: /
Username: guest
Password: *****
Heartbeat: 0
Publisher Confirmation: False
Running Message Latency Benchmark
Message Count: 100000
Clients: 100
Durable: False
Payload Length: 0
Prefetch Count: 1000
Concurrency Limit: 0
Total send duration: 0:00:09.1151465
Send message rate: 10970.75 (msg/s)
Total consume duration: 0:00:09.765957
Consume message rate: 10239.65 (msg/s)
Concurrent Consumer Count: 10
Avg Ack Time: 8ms
Min Ack Time: 0ms
Max Ack Time: 214ms
Med Ack Time: 5ms
95t Ack Time: 29ms
Avg Consume Time: 714ms
Min Consume Time: 246ms
Max Consume Time: 963ms
Med Consume Time: 770ms
95t Consume Time: 908ms

  246ms ****                                                         (   2272)
  318ms ****                                                         (   2219)
  389ms ******                                                       (   3235)
  461ms ***********                                                  (   5605)
  533ms ******************************                               (  14327)
  604ms *************************                                    (  11927)
  676ms ***************                                              (   7403)
  748ms **********************************                           (  16409)
  819ms ************************************************************ (  28472)
  891ms *****************                                            (   8130)
Host: localhost
Virtual Host: /
Username: guest
Password: *****
Heartbeat: 0
Publisher Confirmation: False
Running Request Response Benchmark
Message Count: 100000
Clients: 100
Durable: False
Prefetch Count: 1000
Concurrency Limit: 0
Total consume duration: 0:00:20.6300097
Consume message rate: 4847.31 (msg/s)
Total request duration: 0:00:20.6330248
Request rate: 4846.60 (msg/s)
Concurrent Consumer Count: 25
Avg Request Time: 20ms
Min Request Time: 4ms
Max Request Time: 104ms
Med Request Time: 20ms
95t Request Time: 25ms
Avg Consume Time: 5ms
Min Consume Time: 0ms
Max Consume Time: 54ms
Med Consume Time: 4ms
95t Consume Time: 9ms

Request duration distribution
    4ms                                                              (    527)
   14ms ************************************************************ (  92393)
   24ms ****                                                         (   6736)
   34ms                                                              (    227)
   44ms                                                              (     17)
   84ms                                                              (     16)
   94ms                                                              (     83)
```
