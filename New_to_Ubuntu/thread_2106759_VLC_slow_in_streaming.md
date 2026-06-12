---
title: "VLC slow in streaming"
date: 2013-01-20
forum: New to Ubuntu
---

### Post by shikhar_sharma on 2013-01-20
Hi All,

I have a windows server 2003 as a file share server at my home which i access via my ubuntu 12.10 laptop. I access it via windows share to watch movies stored in that server. I've tried using VLC and Movie player and both of them are giving me strange problems.

In Movie player 3.4.3 , i can't seem to forward a clip...if i try that the movie stops and starts playing from the beginning...(highly frustrating)..so it becomes impossible to watch a movie on it.

In VLC (2.0.5) twoflower if i forward the movie then it takes forever to reach over there, but it does. This is also very frustrating.

Now i know that this is not a network issue, because i got three other  laptops in my home running windows and they don't face any latency  whatsoever using either windows movie player or VLC. It works just fine  over there... This has to do something with my laptop only.

Also i have a windows XP runnin in virtual box on the same laptop. For testing purposes, i installed VLC in that and tried accessing the same movies folder from that server...I used VLC for this and it gave me same exact problem...don't know what to do..

Please help.....

PS: I just migrated from windows to ubuntu, because i want to learn linux, but i think these kind of issues are the one which stops normal users to migrate from windows.

Thanks,
Shikhar Sharma

---

### Post by cariboo on 2013-01-20
First off, why would expect XP running in vbox to work any better, it's using the same hardware as Ubuntu?

Have you checked network speeds? iperf is available for Linux, OSX and Windows, it will allow you to check network speeds on your internal network. iperf is in the repostoris, so all you have to do is install the windows version available [here]("http://linhost.info/2010/02/iperf-on-windows/") it's a command line utility, so you have to start it as a server on one system and a client on the other system.

To start iperf as a server type the following command:

```
iperf -c
```

on the client type:

```
iperf -c server_hostname
```

you should get an output that looks similar to this, from the server:

```
iperf -s
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.0.240 port 5001 connected with 192.168.0.102 port 42119
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.1 sec   113 MBytes  93.7 Mbits/sec
```

and on the client:

```
iperf -c likely
------------------------------------------------------------
Client connecting to likely, TCP port 5001
TCP window size: 22.9 KByte (default)
------------------------------------------------------------
[  3] local 192.168.0.102 port 42119 connected with 192.168.0.240 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec   113 MBytes  94.6 Mbits/sec
```

I have a 100Mbps network, so 94.6Mbits/sec is acceptable as far as I'm concerned.

---

### Post by shikhar_sharma on 2013-01-20
thanks for replying....but i think you missed the part where i said that network speed is not an issue...the only reason being my 3 other windows laptops can stream without any issues....and till 2 days ago when i was using windows on this machine everything worked fine....so network issue is not the case over here....and by the way, i can say this with utmost confidence bcoz i'm a network specialist in cisco....this is what i do....so be assured that this is not a network issue...

any other thoughts ?

---

