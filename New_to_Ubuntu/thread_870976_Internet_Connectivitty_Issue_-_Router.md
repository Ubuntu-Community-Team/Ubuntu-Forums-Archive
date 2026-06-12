---
title: "Internet Connectivitty Issue - Router"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by benditlikebecker13 on 2008-07-26
So I am using Hardy for the second time around andhaving an really annoying problem with my internet connection.  My connection goes down every 10 minutes and the only way to get it back is to reset the router.  The really bizarre thing is that I can't get anywhere in Firefox when this happens, but my Bittorrent client will work just fine.  I don't know what else to say, but I will give some info.  Here is what I get from **ifconfig**:
> 
eth0      Link encap:Ethernet  HWaddr 00:11:2f:34:11:9f  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:2fff:fe34:119f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6891869 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8346233 errors:0 dropped:0 overruns:4 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3410626998 (3.1 GB)  TX bytes:3386969628 (3.1 GB)
          Interrupt:21 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1740 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1740 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:87000 (84.9 KB)  TX bytes:87000 (84.9 KB)


I'm not sure what else you need.  Thanks for your help.

EDIT:  Some other useful info.  I have a Netgear router, I connect with a hard wire (RJ45 from router to CPU) and when I am logged into Ubuntu my PS3 will not go online and gives me a DNS error.

2nd Edit:  It's not the IPv6 issue I have read in other threads.  I went to the following link and got the output I should've.

[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

---

### Post by benditlikebecker13 on 2008-07-28
Bump

---

### Post by halitech on 2008-07-28
if your torrents still work then its nothing to do with your router, its something to do with firefox. when the connection goes down again, open a terminal (before doing anything to the router) and type 
```
ping www.google.ca
``` and post back what happens

---

