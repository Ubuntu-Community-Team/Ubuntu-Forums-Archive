---
title: "Wireless help needed (HARDY)! have tried everything! (BROADCOM BCM4318)"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by Diana_Woods on 2008-06-22
Hi everyone. I've tried browsing the forums for information already posted on this,  but I've been having difficulties with instructions. [I started to get some help in a previous post, but I have a wired connection now so the requirements of the old post no longer apply]

I know this is a common issue and I hope to initiate a discussion that is helpful to myself and others.

I need to be able to scan for wireless networks in different places (cafe, library) with my laptop, and then connect to the unprotected ones without WEP etc. I can't for the life of me figure out how to do this with Hardy!

Do I need to install something separately that SCANS for wireless networks? 

here is some information that may be useful to those who are in the know:

diana@garden:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:c0:9f:e1:14:ca
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 ip=192.168.10.109 latency=173 maxlatency=11 mingnt=52 module=sis900 multicast=yes
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a4:3b:e5:f6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


A thousand thank yous to whoever can help me resolve this.

---

### Post by billgoldberg on 2008-06-22
From what I've read after googling your wireless card (BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller), it should work with ndiswrapper.

Ndiswrapper allows you to use windows drivers in linux for wireless cards.

You'll need the window (xp) driver from the cd that came with your card (or download it from the manufacturers website).

A guide on how to set up ndiswrapper can be found here:

[http://www.tuxmagazine.com/node/1000167](http://www.tuxmagazine.com/node/1000167)

It might be easier to just use an [supported wireless usb adapter]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-603c9481d6c6288b6b674cc50132d21f6d539c53").

---

### Post by mehtdosa11 on 2008-06-22
whilst i'm not expert enough to get your wireless working, i can't tell from your message if it is or not. .

however with regards to scanning for networks, if and when it is working, you don't need anything extra i do believe. you only need to left click on the wireless icon in your top bar and it will give you a drop down list of the available wireless networks in range.

simply select the one applicable to wherever you are and it will ask you for the network key [if needed] obviously the unprotected ones don't use one.

i for instance can connect to my own unsecured fon network at home immediately. i do of course use the secured network which is also available.

i also use [in another laptop] a comtrend wireless card which has the ralink rt2500 chip in it. this chip is supported by most linux os's straight 'out of the box'.

it doesn't support wpa so you can only mostly pick up the wep and unsecured networks. perfect for travelling around! it only cost £12 from a well known linux emporium on the net. might be a quick answer to your problem..

---

### Post by yipperzz on 2008-06-22
so are you having a difficult time trying to install the drivers for the bcm4318?  there are a lot of articles out there that have good instructions, but i can try to help you if i can.  i'm running a bcm4306 and had a difficult time getting it installed also.  but now i'm up and running and scanning for networks around my neighborhood without any issues.

what have you tried to do so far?  do you have the windows driver and installed ndiswrapper?

---

### Post by Pjotr123 on 2008-06-22
This simple and effective how-to will probably do the job for you:
[http://ubuntutip.googlepages.com/nointernetconnection](http://ubuntutip.googlepages.com/nointernetconnection)

Greetz, Pjotr.

---

### Post by Diana_Woods on 2008-06-23
Thank you so much!

I finally got it working!

thank goodness.. I am switched over to Ubuntu completely now... and loving it!

---

