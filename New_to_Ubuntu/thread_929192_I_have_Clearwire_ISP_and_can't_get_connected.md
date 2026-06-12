---
title: "I have Clearwire ISP and can't get connected"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by SeaKona on 2008-09-24
I have Ubuntu and Vista as a dual boot on my pc. I can access the web from windows but nothing from Ubuntu. I am a newbie and had to struggle just to get as far as getting Ubuntu on my PC but now I am stuck with getting an internet connection. My ISP is Clearwire.

I have read that many others are having problems with Clearwire and Ubuntu. I called Clearwire for their help support they told me the system supports linux but they don't have tech support for it.  

Looking for any solutions (other than switching back to Comcast)

Marti

---

### Post by lwvmobile on 2008-09-24
Can you give us a little detail on how you connect in Windows? Is Clearwire a Cable, DSL, Satellite provider? Do you have a static or dynamic ip address? Do you need to use special software in windows or do you use a protocol like PPPOE?

I don't know why you wouldn't be able to get an ISP working, unless it requires special software or a special hardware modem or something.

:popcorn::KS

---

### Post by lwvmobile on 2008-09-24
OK I just googled it, its a cellular provider. 

Your best bet may be using ndiswrapper combined with the drivers they have on their website. Hopefully the authentication onboard the adapter so that is functions more like a gateway/router  than a network card so we can eliminate special software.

BTW, whats your Ubuntu knowledge level? Complete Novice, Beginner, or Intermediate?

---

### Post by crazyone on 2008-09-24
do u got the clearwire pcmcia card or the modem form them cause i got the modem and it works great in linux

---

### Post by SeaKona on 2008-09-24
I am very new to Ubuntu, I am using Hardy Heron 8.04 I am using Clearwire modem not the PCMCIA card. I have been able to connect directly to the modem with Vist without any software and I have also been able to connect through with my D-link wireless router.
Marti

---

### Post by NewDisciple on 2008-09-24
Clearwire pretty much works out of the box on ubuntu.  You didn't provide any info about your computer; hint, hint.  I'm guessing that you may have a hardware specific issue and may need a certain driver.  Perhaps if you provide the previously mentioned information someone will see it that can answer your question.

---

### Post by ckunzler on 2009-01-08
> **NewDisciple said:**
> Clearwire pretty much works out of the box on ubuntu.  You didn't provide any info about your computer; hint, hint.  I'm guessing that you may have a hardware specific issue and may need a certain driver.  Perhaps if you provide the previously mentioned information someone will see it that can answer your question.

I'm also a newbie with clearwire.  Though luckily I've never had a problem with Ubuntu connecting with using Clearwire -- and yes it has always worked out of the box.

---

### Post by dgammon7244 on 2009-04-28
I have ClearWire and i am using the PC Express Card..... dont know much about linux (Ubuntu) If i can get the internet to work and function to where i can do every day task i will leave VISTA BEHIND!!!!! Beside i have always kinda wanted to go to linux just have not had time to learn to use it! I can get the Residential modem to work from clearwire it uses a standard rj connection ethernet..... i switched from that to a pc express card and now i cant get connected using that! Any help on how to use the ndswrapper?

---

### Post by NewDisciple on 2009-04-28
**I have never used ndswrapper myself as I had the Intel 1394 card.  After a while I began having problems with network manager and I switched to WICD, but as I understand it, network manager is vastly improved.  As far as ndswrapper there are many, many threads in the forums with instructions.  As an after thought, you didn't give any specifics on your equipment.  On my laptop eth0 (wired) had to be disconnected first, prior to connecting to eth1 (WLAN0).  The names may be different on your setup but they still mean the same thing.**

---

### Post by dgammon7244 on 2009-04-29
I do not know how to do anything in ubuntu.....

The PC Express Card it self is a that acts as a nic card.

Dont know much about it..... i am trying to use the ndiswrapper and the windows drivers but cant seem to get the ndiswrapper to work cause i am used to windows and dont know how to run or install apps in ubuntu..... i am a newb. to ubuntu a geek at windows..... so i need some help.

---

### Post by NewDisciple on 2009-04-29
[B]Forget about clearwire for the moment as that is not your issue.  Tell us what your computer specs are. Brand & model of motherboard.  Copy & paste: sudo lshw -C net   into your terminal.  It will give net interfaces with output like following example:
rick@ricks-laptop:~$ sudo lshw -C net 
[sudo] password for rick: 
  *-network               
       description: Wireless interface 
       product: PRO/Wireless 3945ABG Network Connection 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0000:0c:00.0 
       logical name: eth1 
       version: 02 
       serial: 00:13:02:08:cd:2b 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () latency=0 link=no module=ipw3945 multicast=yes wireless=unassociated 
  *-network 
       description: Ethernet interface 
       product: BCM4401-B0 100Base-TX 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:14:22:eb:fb:8c 
       size: 100MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=full ip=192.168.1.101 latency=64 link=yes module=b44 multicast=yes port=twisted pair speed=100MB/s 

Of course the names will be different than what I have posted.  This example was from my laptop.  
Here is an example from my desktop:
rick@rick-desktop:~$ sudo lshw -C net 
[sudo] password for rick: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:d0:d0:bb:27
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.100 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 02
       serial: 00:1f:d0:80:e1:65
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:b6:4f:d9:d4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rndis_wlan driverversion=22-Aug-2005 firmware=Wireless RNDIS device, BCM4320b usb-0000:00:1d.7-2 link=yes multicast=yes wireless=IEEE802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: fa:0b:8d:c5:06:0c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

In my previous post I had said I used 1394, oops, thats firewire.  What I meant was the 3945 wireless.  Hope I didn't confuse anyone with that.
Anyhow, post the requested information then we'll have something to work with.[/B]

---

### Post by dgammon7244 on 2009-04-29
drew@ubuntu:~$ sudo lshw -C net
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:17:31:c8:98:cc
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:42:ad:87
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ca:95:bf:69:fc:35
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
drew@ubuntu:~$ 

There this card is in my pc express slot not a regular pc card.
might get it to work if i could find a way to get on the internet some how and get ndiswrapper and the inf. file for the card!

---

### Post by dgammon7244 on 2009-04-29
The card info.

Expedience Broadband Express Card
Model: PCEx25100

from Clearwire.

---

### Post by NewDisciple on 2009-04-30
[B]The BCM43xx and BCm44xx modules require different drivers.  Here are three threads to walk you through this.
[]("http://ubuntuforums.org/showthread.php?t=722938")
[http://ubuntuforums.org/showthread.php?t=649237]("http://ubuntuforums.org/showthread.php?t=649237")
[http://ubuntuforums.org/showthread.php?t=511343&highlight=broadcom+4401]("http://ubuntuforums.org/showthread.php?t=511343&highlight=broadcom+4401")
These links are several years old so I'm not certain that you would still have to compile the 44xx drivers from source and the driver is a newer version that what is talked about in theses threads.  But they will provide some insight, such as how to check your installation.  Now part of this I'm just guessing on as it has been a while since I've had wireless and I never had the Broadcom module.  
Also, you need to activate the desired network in network manager.  To the best of my knowledge only one can be activated at a given time.
The other thing that I wanted to mention is that my modem is old; guess I was one of their first customers.  Until I just now looked it up I have never seen a pci card like yours.  On my modem you plug into the router or directly to the computer.  I don't know if any of this is helping you or just mucking the water. [/B]

---

### Post by NewDisciple on 2009-04-30
**PS: Don't forget that your wireless (eth1) is the BCM 4311.  Your ethernet connection/interface (eth0) is BCM 4401.  Big difference here.  Just to narrow things down a bit, which one are you trying to connect through?**

---

