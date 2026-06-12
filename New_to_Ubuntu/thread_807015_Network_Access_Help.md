---
title: "Network Access Help"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by CTWRYE on 2008-05-25
This is my first attempt at using Linux. This is also my first attempt at posting a question on the Forum.

I am trying to get on line using my home network Ethernet router. I have several other PCs connected and they work fine. This PC has two operating systems on it, and I have no trouble getting on line from the Windows XP Home edition OS partition.

When I use the ifup command in Terminal this is the response I get:

ctwrye@ctwrye-desktop:~$ sudo ifdown eth0
[sudo] password for ctwrye:
There is already a pid file /var/run/dhclient.eth0.pid with pid 5186
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:e0:4c:77:61:68
Sending on   LPF/eth0/00:e0:4c:77:61:68
Sending on   Socket/fallback

ctwrye@ctwrye-desktop:~$ sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:e0:4c:77:61:68
Sending on   LPF/eth0/00:e0:4c:77:61:68
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
ctwrye@ctwrye-desktop:~$ 

I am using a generic PC with an Intel Pentium 4 processor and 1 Gb of memory. The PC is connected to a D-Link DSS 8+ 10/100 Fast Ethernet Switch by cable. This in turn, is connected to a D-Link DI-624 Wireless Router. The router is connected to a Motorola SB1501 Surfboard Cable Modem. 

My ISP is Comcast and I live in the USA.

I am running Ubuntu 8.04

I have no trouble getting on line from any of the Windows XP computers on my home network. On the Windows PCs I use Network Magic to manage my network.

I will be transferring this file to a Windows PC to post to this forum.

Below is the output from Terminal for the commands specified:

ctwrye@ctwrye-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface 

(rev 03)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 

(rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 

(rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 

(rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio 

Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV200 QW [Radeon 7500]
02:0c.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
02:0c.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
02:0c.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
02:0c.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
02:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0e.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
ctwrye@ctwrye-desktop:~$ 
ctwrye@ctwrye-desktop:~$ 

ctwrye@ctwrye-desktop:~$ lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 008 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 057b:0020 Y-E Data, Inc. HEXA Media Drive 6-in-1 Card Reader Writer
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
ctwrye@ctwrye-desktop:~$ 

ctwrye@ctwrye-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: d
       bus info: pci@0000:02:0d.0
       logical name: eth0
       version: 10
       serial: 00:e0:4c:77:61:68
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list Ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 

mingnt=32 module=8139too multicast=yes
ctwrye@ctwrye-desktop:~$ 

I hope there is enough info here to help me resolve my problem. 

Thanks in advance for your help. :)

---

### Post by bwhite82 on 2008-05-25
Please post the results of two additional commands:

> sudo ifconfig -a

and

> cat /etc/network/interfaces

---

### Post by CTWRYE on 2008-05-25
Here are the new commands you requested.

ctwrye@ctwrye-desktop:~$ sudo ifconfig -a
[sudo] password for ctwrye:
eth0      Link encap:Ethernet  HWaddr 00:E0:4C:77:61:68  
          inet6 addr: fe80::2e0:4cff:fe77:6168/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:753 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:157277 (153.5 KB)  TX bytes:7466 (7.2 KB)
          Interrupt:20 Base address:0xc000 

eth0:avah Link encap:Ethernet  HWaddr 00:E0:4C:77:61:68  
          inet addr:169.254.6.106  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:20 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8368 (8.1 KB)  TX bytes:8368 (8.1 KB)

ctwrye@ctwrye-desktop:~$ 
ctwrye@ctwrye-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth0
ctwrye@ctwrye-desktop:~$

---

### Post by spiderbatdad on 2008-05-25
I have a similar issue on one pc. I find the following works:```
sudo ifdown eth0
sudo dhclient
```

---

