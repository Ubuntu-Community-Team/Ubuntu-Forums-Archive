---
title: "[SOLVED] network tools?"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by steve allen on 2008-05-18
In network tools only the devices page seems to have any settings on it, the rest are all blank is this normal.

Also in devices the network device is set to loopback interface (lo) is this right what does it mean.

---

### Post by neur0 on 2008-05-18
Well, they shouldn't be completely blank, just need to have empty fields to recieve input. Having loopback in the list is normal, you should have other interfaces in that list.
What interfaces are listed when you type "ifconfig" in the Terminal ?

---

### Post by neur0 on 2008-05-18
Double-post sorry...
dunno how to delete..

---

### Post by steve allen on 2008-05-18
ifconfig gives the following:-

eth0      Link encap:Ethernet  HWaddr 00:1c:25:2e:40:d6  
          inet6 addr: fe80::21c:25ff:fe2e:40d6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:538 (538.0 B)  TX bytes:492 (492.0 B)
          Base address:0xec00 Memory:feae0000-feb00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1732 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1732 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:86600 (84.5 KB)  TX bytes:86600 (84.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:2a:1f:92:d7  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:2aff:fe1f:92d7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35282 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22755 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:51794440 (49.3 MB)  TX bytes:2061724 (1.9 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1E-2A-1F-92-D7-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Its all greek to me!!!!!

---

### Post by logx on 2008-05-18
To me it looks more like Turkish...:p

What are you trying to do? Problem with the network connection?

---

### Post by steve allen on 2008-05-18
Yes trying to network to get files off other computer (win xp) before I switch that one to ubuntu as well

Also trying to get wireless going but I think I may have made a bad choice (as far as ubuntu users go) of choosing to use a netgear usb adapter

Wireless now up and running just netwoking with xp to sort.

---

