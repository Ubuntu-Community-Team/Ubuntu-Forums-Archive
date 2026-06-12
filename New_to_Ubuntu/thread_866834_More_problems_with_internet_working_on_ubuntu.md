---
title: "More problems with internet working on ubuntu"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by AnonUK on 2008-07-22
Ok,well i have a wired router. The internet works on vista, but not on ubuntu. I think the internet fails on ubuntu when i reset my router (turn it off when im sleeping).

here is ifconfig on ubuntu:

root@anonymous-desktop:~# ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:19:db:43:22:de   
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0 
          inet6 addr: fe80::219:dbff:fe43:22de/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:4430 (4.3 KB)  TX bytes:5130 (5.0 KB) 
          Interrupt:21 Base address:0xc000  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:2624 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:2624 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:131200 (128.1 KB)  TX bytes:131200 (128.1 KB) 
 

this is route

root@anonymous-desktop:~# route 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0 
link-local      *               255.255.0.0     U     1000   0        0 eth0 
default         192.168.0.1     0.0.0.0         UG    100    0        0 eth0 


this is ipconfig on vista



Windows IP Configuration


Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . : home
   Link-local IPv6 Address . . . . . : fe80::908c:e299:9623:2440%8
   IPv4 Address. . . . . . . . . . . : 192.168.0.2
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.0.1

Tunnel adapter Local Area Connection* 6:

   Connection-specific DNS Suffix  . : home
   Link-local IPv6 Address . . . . . : fe80::5efe:192.168.0.2%16
   Default Gateway . . . . . . . . . :

Tunnel adapter Local Area Connection* 9:

   Connection-specific DNS Suffix  . :
   IPv6 Address. . . . . . . . . . . : 2001:0:d5c7:a2ca:103d:182f:a53c:5b72
   Link-local IPv6 Address . . . . . : fe80::103d:182f:a53c:5b72%9
   Default Gateway . . . . . . . . . : ::

Tunnel adapter Local Area Connection* 10:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Tunnel adapter Local Area Connection* 11:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Tunnel adapter Local Area Connection* 12:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Tunnel adapter Local Area Connection* 7:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :



on ubuntu i tried 

sudo ifconfig eth0 192.168.0.2

and it didn't work :S  help please

---

### Post by sharks on 2008-07-22
do u have ethernet connection? 

try

sudo pppoeconf 
and configure .

---

### Post by Potatoj316 on 2008-07-22
Are you using IPv6 on vista?  Thats what it looks like to me.  It also seems that your computer is not trying to get an IP when running ubuntu.  Im not sure what the command is to tell it to get one.  You have DHCP on your router right?

---

### Post by superprash2003 on 2008-07-22
go to system->admin->network and go to eth0 properties and set it to DHCP.. then type ifconfig and see what ip you are getting.. then type ping 192.168.0.1 in your terminal and post output

---

