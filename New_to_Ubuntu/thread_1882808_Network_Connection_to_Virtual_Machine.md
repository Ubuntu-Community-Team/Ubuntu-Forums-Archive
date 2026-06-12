---
title: "Network Connection to Virtual Machine?"
date: 2011-11-18
forum: New to Ubuntu
---

### Post by greendragons on 2011-11-18
Hello,
I am using Ubuntu 11.04 and running Slackware on virtual box, i am unable to connect Slackware to Ubuntu..
```

root@darkstar:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 08:00:27:17:7f:3d  
          inet6 addr: fe80::a00:27ff:fe17:7f3d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:238 (238.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2140 (2.0 KiB)  TX bytes:2140 (2.0 KiB)

root@darkstar:~# ping 10.116.28.218
connect: Network is unreachable



```while on Ubuntu vmboxnet0 is up..... where 10.116.28.218 is ip of host system...
how to setup connection between my ubuntu machine and my virtual machine....


Thnx!!

---

