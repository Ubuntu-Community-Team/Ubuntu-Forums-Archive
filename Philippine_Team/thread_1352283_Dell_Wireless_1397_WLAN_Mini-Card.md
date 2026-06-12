---
title: "Dell Wireless 1397 WLAN Mini-Card"
date: 2009-12-11
forum: Philippine Team
---

### Post by junebhryan on 2009-12-11
Mabuhay!!! 

Hi, Newbie here for QC!

I installed Ubuntu 9.10 in my Dell Inspiron 1440 using Wubi to have a dual OS boot (VISTA SP2). Everytime I boot using Vista I can connect wireless and hardwired but if I boot using Ubuntu my hardwired connection works however my wireless connection doesn't work. It can't identify the any wireless network. I already tried to configure the SSID, MAC and WPA encryption in the wireless network and still won't connect.

I tried to search online to resolve my issues but most of the things are too ambiguous for me to understand so far these are the things I was able to find..

WLAN Card Data

Dell Wireless 1397 WLAN Mini-Card
driver provider broadcom
driver date 10/22/2008
driver version 5.10.38.26
digital signer microsoft windows hardware compatibility published


using sudo lshw -C network

*-network
description: Network controller
product: BCM4312 802.11b/g
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:0c:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: driver=b43-pci-bridge latency=0
resources: irq:17 memory:f69fc000-f69fffff
*-network
description: Ethernet interface
product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:09:00.0
logical name: eth0
version: 02
serial: 00:25:64:5b:9a:66
size: 100MB/s
capacity: 100MB/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.100 latency=0 link=yes multicast=yes port=MII speed=100MB/s
resources: irq:29 ioport:de00(size=256) memory:f0010000-f0010fff(prefetchable) memory:f0000000-f000ffff(prefetchable) memory:f0020000-f003ffff(prefetchable)

Maraming salamat sa inyong pagtulong!!!

Thanks!

---

### Post by piojunbabia on 2009-12-11
same problem with my sisters laptop.. lan is working but wireless wont... she using Acer blah blah...im using desktop and we are lan...

---

### Post by junebhryan on 2009-12-11
Guys,
 
I was able to search online and found this site... [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)
 
when I check my WLAN PCID it is 14e4:4315 - in progress of being supported because of LP.
 
:sad:

I will just keep on searching to get my wireless connection working.
 
If you any other suggests that you think could help... Please post it! I beg you!
 
Nalulungkot at nagmamakaawa! 
 
-junebhryan

---

### Post by loell on 2009-12-11
if the PCID is  **14e4:4315** 

then this howto would most probably work, [http://ubuntuforums.org/showthread.php?t=1266620](http://ubuntuforums.org/showthread.php?t=1266620)

---

### Post by junebhryan on 2009-12-11
I will try it and hopefully it will work!
 
 
Thanks!

---

### Post by ublintu on 2009-12-12
maybe here the second and third posts can be helpful as well:
[http://ubuntuforums.org/showthread.php?t=1352270&highlight=broadcom](http://ubuntuforums.org/showthread.php?t=1352270&highlight=broadcom)
(if you don`t have cable internet connection, you can try the third one.)

---

### Post by junebhryan on 2009-12-14
[SIZE=3]hehehe!!!

Mabuhay ulit!!!
[/SIZE] 			 		   		 		
[SIZE=3]
I was able to make my wireless connection work... This I how I did it. I activated the Broadcom b43 wireless driver from Hardware Drivers. Then opened Synaptic Package Manager and installed bcmwl-kernel-source making sure that in the Repository, CDrom with Ubuntu 9.10 'karmic koala' is not checked because I have hardwired internet connection . Reloaded then applied the settings. Restarted the computer. Configured my wireless connection. Able to browse. Issue resolved.

Thanks for the help![/SIZE]

---

### Post by jrsii75 on 2010-11-21
> **junebhryan said:**
> [SIZE=3]hehehe!!!

Mabuhay ulit!!!
[/SIZE]                                          
[SIZE=3]
I was able to make my wireless connection work... This I how I did it. I activated the Broadcom b43 wireless driver from Hardware Drivers. Then opened Synaptic Package Manager and installed bcmwl-kernel-source making sure that in the Repository, CDrom with Ubuntu 9.10 'karmic koala' is not checked because I have hardwired internet connection . Reloaded then applied the settings. Restarted the computer. Configured my wireless connection. Able to browse. Issue resolved.

Thanks for the help![/SIZE]

After spending over a dozen days and countless hours of trying to figure this thing out and which lead to a lot of online research.  This my friend is the ONLY way solution to this problem.  THANKS  a bunch for sharing this information.  Everyone reading this thread, this is by far the best solution PERIOD!! BAR NONE!!!:biggrin:=D>:popcorn:

---

### Post by zdenal on 2010-12-02
I had same problems with Broadcom driver on Lucid and Maverick.

In my post

[http://polach.cc/broadcom-wifi-adapter-wpa-access-fix-on-ubuntu-ii](http://polach.cc/broadcom-wifi-adapter-wpa-access-fix-on-ubuntu-ii)

I summarize some facts so you can check

a) If your Broadcom card is supported by the wl.ko driver
b) Use step by step HowTo to try fix your wireless problem

Hope this helps..

---

