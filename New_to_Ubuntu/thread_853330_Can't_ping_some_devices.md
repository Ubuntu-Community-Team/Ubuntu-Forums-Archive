---
title: "Can't ping some devices"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by el.demiurgo on 2008-07-08
Hi everyone!
I am new in Ubuntu. I like it a lot but I am having some problems with networking.
I can't ping my Xbox, router, Xbox360 or other PC in my network from my wireless adapter. It works from the wired one though.

I do have internet access from both adapters.

I don't have any firewall installed I believe.

My ifconfig shields:
eth0 Link encap:Ethernet HWaddr 00:0e:a6:bc:dc:59
inet addr:192.168.0.201 Bcast:192.168.0.255 Mask:255.255.255.0
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:20

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:2128 errors:0 dropped:0 overruns:0 frame:0
TX packets:2128 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:133171 (130.0 KB) TX bytes:133171 (130.0 KB)

wlan0 Link encap:Ethernet HWaddr 00:19:5b:80:03:19
inet addr:192.168.0.109 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::219:5bff:fe80:319/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:4859 errors:0 dropped:0 overruns:0 frame:0
TX packets:4897 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:2175495 (2.0 MB) TX bytes:810932 (791.9 KB)

wmaster0 Link encap:UNSPEC HWaddr 00-19-5B-80-03-19-00-00-00-00-00-00-00-00-00-00
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)



Thanks for your help!

---

### Post by dca on 2008-07-08
You don't have both an ethernet cable connected and active plus your wireless hitting (connected to) the router at the same time do you?  
 
...nevermind, I can see above that you don't...
 
...the only other thing I can think of is the wireless router has MAC address filtering active and one of the MACs is missing from one of the NICs or router firewall settings.  Geez, the more I think about it there could be quite a few culprits.

---

### Post by el.demiurgo on 2008-07-08
Thanks DCA for your help. I don't have both active at the same time, I always use wireless.

I also can confirm that my router isn't filtering it. This machine is a dual boot (XP) and it works ok in windows.

I have to suspects but I don't know how to handle.
The first one is that wlan0 has an extra line: inet6 addr: fe80::219:5bff:fe80:319/64 Scope:Link
I presume this is some IPV6 stuff I don't know how to turn it of.

THe other suspect is UFW. Using terminal I see that's off but I am not sure since when the machine is booting down I can see a sign that states the UFW is on (¿?).

I am really lost....

---

### Post by dca on 2008-07-08
This may help but I don't recommend because I can ping my routers w/ IPv6 enabled...
 
[http://ubuntuforums.org/showthread.php?t=6841](http://ubuntuforums.org/showthread.php?t=6841)

---

### Post by el.demiurgo on 2008-07-08
I'll try this. Thank you!!

---

### Post by dca on 2008-07-08
Have you checked the wireless router to make sure it accepts ICMP (ping) requests because it sure sounds to me the problem is at the router, not IPv6 being enabled on your Ubuntu box...

---

### Post by el.demiurgo on 2008-07-08
ICMP is on. This is strange because is not only "ping" the problem. From my wired connection (to the same router) I can ping, transfer files, internet, etc. The only thing I can do from the wireless adapter is use internet.

It seems that the problem is some kind of firewall that I don't know how to handle.

---

