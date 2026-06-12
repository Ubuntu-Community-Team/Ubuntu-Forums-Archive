---
title: "Having wifi problems 14.04 Sony Vaio"
date: 2014-05-02
forum: New to Ubuntu
---

### Post by alex191 on 2014-05-02
How do i know what Wireless card im running so i can start fixing my conection problem?

---

### Post by piotrasbl on 2014-05-02
ifconfig in console should give you all the answers.

---

### Post by alex191 on 2014-05-02
This is what i got

-PCG-V505BX-UC:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 08:00:46:ad:24:9c  
          inet addr:192.168.1.136  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:46ff:fead:249c/64 Scope:Link
          inet6 addr: 2602:306:bc9a:c760:8d37:7783:b9a3:ccb4/64 Scope:Global
          inet6 addr: 2602:306:bc9a:c760:a00:46ff:fead:249c/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2286 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1539 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1420420 (1.4 MB)  TX bytes:201962 (201.9 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:723 errors:0 dropped:0 overruns:0 frame:0
          TX packets:723 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:64734 (64.7 KB)  TX bytes:64734 (64.7 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-02-8A-94-E4-F5-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:9 Base address:0xe000 

wlan0     Link encap:Ethernet  HWaddr 00:02:8a:94:e4:f5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:9 Base address:0xe000

---

