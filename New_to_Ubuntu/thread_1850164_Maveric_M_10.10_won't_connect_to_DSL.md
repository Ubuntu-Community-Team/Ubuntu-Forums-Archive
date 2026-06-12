---
title: "Maveric M 10.10 won't connect to DSL"
date: 2011-09-25
forum: New to Ubuntu
---

### Post by chris_labonte on 2011-09-25
I'm a beginner.
But this is not a new problem (you all fixed a similar problem for me when it occurred few months ago).

1.  I have checked all hardware (used the same DSL wire to connect to PC)
2. Re Started
3. Also I ran the computer on the startup CD (it did not connect)


I ran ifconfig
and 'sudo dhclient eth0' 

I have pasted the results below - format is off as I needed to cut and paste it.

clabonte@clabonte-ER903AA-ABA-a1424n:~$ ifconfig
eth0 
Link encap:Ethernet HWaddr 00:15:f2:e5:21:90 

inet addr:192.168.0.7 Bcast:192.168.0.255 Mask:255.255.255.0

inet6 addr: fe80::215:f2ff:fee5:2190/64 Scope:Link

UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1

RX packets:48 errors:50 dropped:0 overruns:0 frame:0

TX packets:74 errors:0 dropped:0 overruns:0 carrier:0

collisions:0 txqueuelen:1000 

RX bytes:13581 (13.5 KB) TX bytes:11708 (11.7 KB)

Interrupt:21 Base address:0xe400 

lo 
Link encap:Local Loopback 

inet addr:127.0.0.1 Mask:255.0.0.0

inet6 addr: ::1/128 Scope:Host

UP LOOPBACK RUNNING MTU:16436 Metric:1

RX packets:4 errors:0 dropped:0 overruns:0 frame:0

TX packets:4 errors:0 dropped:0 overruns:0 carrier:0

collisions:0 txqueuelen:0 

RX bytes:240 (240.0 B) TX bytes:240 (240.0 B)



clabonte@clabonte-ER903AA-ABA-a1424n:~$ 


clabonte@clabonte-ER903AA-ABA-a1424n:~$ 

sudo dhclient eth0
[sudo] password for clabonte: 

Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.

All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)


Listening on LPF/eth0/00:15:f2:e5:21:90
Sending on LPF/eth0/00:15:f2:e5:21:90

Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6

DHCPOFFER of 192.168.0.7 from 192.168.0.1

DHCPREQUEST of 192.168.0.7 on eth0 to 255.255.255.255 port 67

DHCPREQUEST of 192.168.0.7 on eth0 to 255.255.255.255 port 67

DHCPREQUEST of 192.168.0.7 on eth0 to 255.255.255.255 port 67

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3

DHCPOFFER of 192.168.0.7 from 192.168.0.1

DHCPREQUEST of 192.168.0.7 on eth0 to 255.255.255.255 port 67

DHCPREQUEST of 192.168.0.7 on eth0 to 255.255.255.255 port 67

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3

DHCPOFFER of 192.168.0.7 from 192.168.0.1

DHCPREQUEST of 192.168.0.7 on eth0 to 255.255.255.255 port 67

DHCPREQUEST of 192.168.0.7 on eth0 to 255.255.255.255 port 67

DHCPREQUEST of 192.168.0.7 on eth0 to 255.255.255.255 port 67

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3

DHCPOFFER of 192.168.0.7 from 192.168.0.1

DHCPREQUEST of 192.168.0.7 on eth0 to 255.255.255.255 port 67

DHCPACK of 192.168.0.7 from 192.168.0.1

bound to 192.168.0.7 -- renewal in 36327 seconds.

clabonte@clabonte-ER903AA-ABA-a1424n:~$

---

### Post by jtarin on 2011-09-26
I don't use Network Manager and never will. Ok...that's out of my system. :)

I always set up my DSL connection manually. Assuming your not using a router and DSL modem only.....[Here]("https://help.ubuntu.com/community/ADSLPPPoE").

---

### Post by chris_labonte on 2011-09-27
Thanks,
This link helped to enlarge my very small circle of knowledge, and to solve my problem.

-C

---

### Post by jtarin on 2011-09-27
Once you learn how to setup your connection without a GUI it becomes more transparent. Anything more on the subject you need help with let me know. Mark the thread as solved then if your satisfied.:P

---

