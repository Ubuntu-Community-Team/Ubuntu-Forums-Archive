---
title: "network configuration issue"
date: 2012-01-03
forum: New to Ubuntu
---

### Post by tompoe on 2012-01-03
I have three computers that at one point all had access to Internet.  I am connected to ISP by DSL modem, which goes to a 4 port switch, and the three computers are connected by cable to the switch.  My computer workstation ifconfig

~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0b:db:70:4d:01  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:dbff:fe70:4d01/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:283381 errors:0 dropped:0 overruns:0 frame:0
          TX packets:161633 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:390344801 (390.3 MB)  TX bytes:14630839 (14.6 MB)

I want to now redo the present state so I have the following setup:
192.168.1.64 remains as is
computer 2 gets assigned a static ip, shares Internet access
computer 3 gets assigned a static ip, shares Internet access

What's best way to do that?  They are all linux computers,

---

### Post by spiky001 on 2012-01-03
Dose this help [http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html](http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html)

---

