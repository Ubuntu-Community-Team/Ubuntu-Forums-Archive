---
title: "One of my two network card doesnot work"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by Guruprasad on 2008-08-30
One of my two network card doesnot work. Below are the details
I am using dual boot. The both networks work fine with windows. So I think there is no problem with cable.


> ifconfig returned
eth0 Link encap:Ethernet HWaddr 00:13:46:8d:cf:95
inet addr:192.168.100.101 Bcast:192.168.100.255 Mask:255.255.255.0
inet6 addr: fe80::213:46ff:fe8d:cf95/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:244 errors:0 dropped:0 overruns:0 frame:0
TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:22981 (22.4 KB) TX bytes:5491 (5.3 KB)
Interrupt:16

> eth1 Link encap:Ethernet HWaddr 00:80:48:42:d3:ed
inet addr:116.68.64.109 Bcast:255.255.255.255 Mask:255.255.248.0
inet6 addr: fe80::280:48ff:fe42:d3ed/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:882 errors:0 dropped:18454 overruns:0 frame:0
TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:54013 (52.7 KB) TX bytes:4099 (4.0 KB)
Interrupt:17 Base address:0xe400

> lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:2320 errors:0 dropped:0 overruns:0 frame:0
TX packets:2320 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:116000 (113.2 KB) TX bytes:116000 (113.2 KB)

> sudo ethtool eth1 showed
Settings for eth1:
Supported ports: [ TP MII ]
Supported link modes: 10baseT/Half 10baseT/Full
100baseT/Half 100baseT/Full
Supports auto-negotiation: Yes
Advertised link modes: 10baseT/Half 10baseT/Full
100baseT/Half 100baseT/Full
Advertised auto-negotiation: Yes
Speed: 100Mb/s
Duplex: Full
Port: MII
PHYAD: 32
Transceiver: internal
Auto-negotiation: on
Supports Wake-on: pumbg
Wake-on: d
Current message level: 0x00000007 (7)
Link detected: yes


---

### Post by neurostu on 2008-08-30
What do you mean your 2nd card doesn't work?  It looks like they both have an IP address...
eth0:192.168.100.101
eht1:116.68.64.109

What are you trying to do with the two cards?

---

### Post by gmxgeek on 2008-08-30
> **neurostu said:**
> What do you mean your 2nd card doesn't work?  It looks like they both have an IP address...
eth0:192.168.100.101
eht1:116.68.64.109

What are you trying to do with the two cards?

They both have an ip address, and both are sending and receiving packets. What is the issue here?

---

### Post by Guruprasad on 2008-08-30
eth0 works fine... eth1 doesnot work...

eth0 is ment for LAN where as eth1 is for broadband internet...

with eth0 I can access all other computers on network...
when I try to open any website browser just says looking up [www.website.com](www.website.com)

---

### Post by gmxgeek on 2008-08-30
> **Guruprasad said:**
> eth0 works fine... eth1 doesnot work...

eth0 is ment for LAN where as eth1 is for broadband internet...

with eth0 I can access all other computers on network...
when I try to open any website browser just says looking up [www.website.com](www.website.com)


Could you explain a little more what exactly you are trying to do with these cards? My understanding it eth0 goes to LAN, and eth1 goes to internet gateway. If you are trying access webpages using eth0, it will not work, since it has no outside internet connection, just a LAN line

---

### Post by Guruprasad on 2008-08-30
In my office I want to switch from windows to Linux. There are 8 computers in office. All of them have single ethernet cards for LAN connection.

Only one computer have two cards as it is connected to internet also. Windows we configure one card of this computer with static IP for LAN and other for automatic DHCP for internet. When we open network places on windows we get other computers on LAN and when we open Mozilla Firefox we get internet.

Now we installed UBUNTU on this system with two network cards. When we click network we get other computer and I suppose it is using eth0 for this. But when I open mozilla firefox and look for wensite it just says looking up [www.websitename.com](www.websitename.com)

I donot know whether Firefox is using eth0 or eth1... is there any more configuration needed...?

---

### Post by gmxgeek on 2008-08-30
> **Guruprasad said:**
> In my office I want to switch from windows to Linux. There are 8 computers in office. All of them have single ethernet cards for LAN connection.

Only one computer have two cards as it is connected to internet also. Windows we configure one card of this computer with static IP for LAN and other for automatic DHCP for internet. When we open network places on windows we get other computers on LAN and when we open Mozilla Firefox we get internet.

Now we installed UBUNTU on this system with two network cards. When we click network we get other computer and I suppose it is using eth0 for this. But when I open mozilla firefox and look for wensite it just says looking up [www.websitename.com](www.websitename.com)

I donot know whether Firefox is using eth0 or eth1... is there any more configuration needed...?

firefox should be piping in the connection from both, however you could try to disable eth0 and see if you have internet then. If so, then there is some sort of sharing confusion among the connections. If not, then you need to get eth1 working before worrying about eth0 as well

---

