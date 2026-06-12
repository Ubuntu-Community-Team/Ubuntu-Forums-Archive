---
title: "[SOLVED] No internet connection"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by rrcs on 2008-07-13
I just installed Xubuntu 8.04 dualboot with Windows XP, and am having problems connecting to the internet (no problem in XP).

I am not sure if I am missing a driver for my network card?

I searched the forum, and tried running sudo pppoeconf, and got the following error message:

> Sorry, I scanned 2 interfaces, but the Access
Concentrator of your provider did not respond. Please
check your network and modem cables. Another reason
for the scan failure may also be another running pppoeprocess which controls the modem.

Output of lspci and ifconfig:

> sisse@sisse-desktop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 735 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:09.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)
00:0b.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8029(AS)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
sisse@sisse-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:80:ad:00:9b:9e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:5 Base address:0xd400 

eth1      Link encap:Ethernet  HWaddr 00:c0:26:11:41:b8  
          inet6 addr: fe80::2c0:26ff:fe11:41b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:468 (468.0 B)
          Interrupt:11 Base address:0xcc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 B)  TX bytes:200 (200.0 B)

Thank you in advance for any help you are able to give!

---

### Post by fahadsadah on 2008-07-13
Odd, your network card should work out of the box!

EDIT: Sorry, I missed something. Try ```
dhclient
```

---

### Post by superprash2003 on 2008-07-13
also try this.. go to system->admin->network and go to eth1 properties and set it to DHCP mode.. and then post ifconfig output again.. you dont seem to be getting an ip in eth1

---

### Post by rrcs on 2008-07-13
Thank you, superprash2003! (Uhm, actually I had seen that solution while searching the forum, but had trouble figuring out how to do it - tried a bit harder to figure it out this time, and finally got it - thanks!)

---

