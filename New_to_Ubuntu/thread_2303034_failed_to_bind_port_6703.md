---
title: "failed to bind port 6703"
date: 2015-11-15
forum: New to Ubuntu
---

### Post by prog-researcher on 2015-11-15
i'm using  version of storm to -0.9.5 with zookeeper-3.4.6 i'm on ubuntu 12.04 LTS via Vmware 

and got with supervisor still hasn't start  with this in the worker log file 

[ERROR] Error on initialization of server mk-worker
org.apache.storm.netty.channel.ChannelException: Failed to bind to: [0.0.0.0/0.0.0.0:6703]("http://0.0.0.0/0.0.0.0:6705")
	at org.apache.storm.netty.bootstrap.ServerBootstrap.bind(ServerBootstrap.java:272) ~[storm-core-0.9.5.jar:0.9.5]

---

