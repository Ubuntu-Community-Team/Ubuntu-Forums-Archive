---
title: "java application (not applet) throws socket error accessing non-private IP"
date: 2011-08-05
forum: Programming Talk
---

### Post by hoink on 2011-08-05
I'm using libshout-java in my java application to stream mp3/ogg to an icecast/shoutcast server.

It connects, but only as long as the ice/shoutcast server is 1) on localhost (on my Ubuntu development machine) or 2) my local private 10...* network.

But when I point the libshout-java code to an internet address, I get a socket error -4 (a shout exception, not a java exception). This failure occurs when running the java code from Eclipse or from the command line.

I've confirmed that other ice/shoutcast streamers running on my Ubuntu development machine can successfully connect to ice/shoutcast internet IPs. But java can't.

Additional detail: the Ubuntu machine is "multi-homed", I guess: it connects to the internet via a wi-fi connection to my router (192...*), and then shares that connection with an ethernet-connected PC connected on a private network (10...*).

---

