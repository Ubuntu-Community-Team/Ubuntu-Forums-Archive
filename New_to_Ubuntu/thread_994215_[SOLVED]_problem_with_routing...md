---
title: "[SOLVED] problem with routing?.."
date: 2008-11-26
forum: New to Ubuntu
---

### Post by vgots on 2008-11-26
Hello,

I have Xubuntu (the same problem appears on ubuntu and kubuntu also, nvm) desktop 8.04 LTS installed on my box just 5 minutes ago... My internet connection is up through ADSL-modem (Acorp, inside of it there's a pppoe option that allows me to connect to the internet). Well, everything works fine for me but one problem is that when I try to connect "to me" with my IP address given by my provider, it always shows the login screen of my modem (mean that everybody who knows my IP can have an access to my modem box)... Maybe it's not a big problem, but when I connect to the internet through DSL connections (say, in 8.10) this problem isn't appear, so when I input my IP address again - no login screen, just my "web-server" (lighttpd)

Can anybody tell me what's the problem, please? How should I solve it?

p.s. maybe the netstat -nr will help:

192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0

---

### Post by Peter09 on 2008-11-26
Is that from an external source, or from the machine which is connected to the modem?

---

### Post by vgots on 2008-11-26
> **Peter09 said:**
> Is that from an external source, or from the machine which is connected to the modem?

yes, my machine is directly connected to the modem (eth0)...

p.s.[2].
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:8c:38:b0:83  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:8cff:fe38:b083/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:56602 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48036 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:67222968 (64.1 MB)  TX bytes:4205996 (4.0 MB)
          Interrupt:220 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:e0:4c:20:48:4c  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:fe20:484c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:91 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2129 (2.0 KB)  TX bytes:14858 (14.5 KB)
          Interrupt:10 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:102 errors:0 dropped:0 overruns:0 frame:0
          TX packets:102 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5100 (4.9 KB)  TX bytes:5100 (4.9 KB)

---

### Post by Peter09 on 2008-11-26
You may find that you modem responds differently coming from your machine. An external connection may not show the internal web page of the modem.

---

### Post by vgots on 2008-11-26
> **Peter09 said:**
> You may find that you modem responds differently coming from your machine. An external connection may not show the internal web page of the modem.

Thanks, so if I've understood you right, should I connect through system not modem? Or is it something else? Well it's just my english, sorry for it, but what's about the problem, is there any way to route a connection somehow that my modem won't "answer" to requests from global network?

---

### Post by vgots on 2008-11-26
anybody? :confused: really need your help...

---

### Post by Peter09 on 2008-11-26
You need to get another machine to connect to your external IP address and see what happens.

---

### Post by vgots on 2008-11-27
> **Peter09 said:**
> You need to get another machine to connect to your external IP address and see what happens.

Well, that login screen appears when anybody connect to me through web-browser, from local network and from global both. Moreover, my lighttpd works just through "localhost;127.0.0.1" etc., and in local network its web-pages are shown only when somebody connect to me through my local IP. Through external IP everybody sees the login screen of my modem :(

---

### Post by vgots on 2008-11-27
Well, I've solved this problem. Just used pppoeconf, now my connection is up through it, very useful and easy I must notice :) Thanks Peter!

---

