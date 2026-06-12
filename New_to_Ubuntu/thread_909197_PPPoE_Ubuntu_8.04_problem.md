---
title: "PPPoE Ubuntu 8.04 problem"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by sloop on 2008-09-03
Hi my friends!Previously I used ubuntu 7.04 with pppoe and had no problem using pppoeconf.But now after procedure with pppoeconf command internet does not work.If I run NETWORK menu sometimes it enables connection, but not allways and after reboot in same manu this connection is not enabled.When I click to enable it, the tick appears and quckly disappears and nothing.Strange but with live cd it is the same.With windows no problem.How to set connection once and for all?

---

### Post by sloop on 2008-09-03
I forgot it is the desktop 64 bits ubuntu 8.04

---

### Post by manishtech on 2008-09-03
when it doesnt work, can you post the output of the command

```
ifconfig
```

---

### Post by sloop on 2008-09-03
ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:19:66:5e:61:1b  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:393 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:24848 (24.2 KB)  TX bytes:6496 (6.3 KB) 
          Interrupt:248 Base address:0x4000 

eth0:avahi Link encap:Ethernet  HWaddr 00:19:66:5e:61:1b  
          inet addr:169.254.4.11  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          Interrupt:248 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:2330 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:2330 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:118612 (115.8 KB)  TX bytes:118612 (115.8 KB) 

ppp1      Link encap:Point-to-Point Protocol  
          inet addr:192.168.195.47  P-t-P:192.168.224.1  Mask:255.255.255.255 
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1 
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:3 
          RX bytes:96 (96.0 B)  TX bytes:94 (94.0 B)

---

### Post by mahiyar on 2008-09-03
Your ppoe is enabled but it gets connected on ppp1 and not on on default ppp0. By right clicking the icon and electing properties you can see which ppp you want to enable. However the point is t hat internet is on and should work. By any chance are you giving more then one command of pon

---

### Post by sloop on 2008-09-03
Thanks, I'll try.

---

