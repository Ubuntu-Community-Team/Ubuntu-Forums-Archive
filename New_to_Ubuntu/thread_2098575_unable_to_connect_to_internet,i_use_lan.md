---
title: "unable to connect to internet,i use lan"
date: 2012-12-27
forum: New to Ubuntu
---

### Post by teejabar on 2012-12-27
hi every body, please am new to ubuntu,i just installed ubuntu server12.04, using lan as my network.But since i installed, i cant download anythg from the net, i cant even update, or upgrade. please does anyone have a clue

---

### Post by xtextedx on 2012-12-27
tried the output of 
$sudo ifconfig
=> to find if it recognises an adapter?
or
$sudo dhclient 
=> see whether you can get a dhcp server to respond? 


Are you installed on bare metal or are you in a virtual machine? 
what do you want to do with your server install? 

Chris.

---

### Post by teejabar on 2012-12-27
the output of $sudo ifconfig is

eth0      Link encap:Ethernet  HWaddr 00:01:6c:64:e0:b4  
inet addr: 192.168.2.114  Bcast:192.168.2.255 Mask:255.255.255.0
inet6 addr: fe80::201:6cff:fe64:e0b4/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2814 errors:0 dropped:3 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:606498 (606.4 KB)  TX bytes:1372  (1.3 KB)
          Interrupt:42

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


Also when i do $ $sudo dhclient , it kept blinking without reply


 i want to install request tracker on my server

---

### Post by teejabar on 2012-12-27
Hi is anyone still there?
please i need reply urgently so that i can continue with my RT installation, and so i will meet up with the deadline of the project. Thanks for your anticipated quick response

---

### Post by teejabar on 2012-12-27
tanks

---

### Post by Cheesemill on 2012-12-27
Please see my reply in your other thread for why you can't install any software.

---

