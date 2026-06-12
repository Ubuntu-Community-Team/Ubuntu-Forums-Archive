---
title: "[SOLVED] wlan0 disabled"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by oiio on 2008-06-14
hello everybody
completely new to the scene after having that one virus to many...

now i want to get my wireless internet running and it doesn't.
in the "help and support" I did a troubleshoot and i think i got the problem.
```

output from "lshw -C network"

  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:c0:9f:b4:61:05
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 ip=192.168.1.31 latency=173 maxlatency=11 mingnt=52 module=sis900 multicast=yes
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
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a4:14:44:2d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
```


...so my wireless is disabled i guess.
but i can't find haw to enable it:(

it's probably very simple but i guess that's why there's an "absolute beginner" topic, right :)

---

### Post by wormser on 2008-06-14
Which version of Ubuntu are you using?  It could be a few things.  Right click on the network icon near the clock and make sure wireless is enabled.  Is this a laptop?  Most laptops have a switch to turn off wireless.  It looks like this is a Broadcom card.  Do you remember how you installed it?  Check under System> Administration> Hardware Drivers (Restricted Drivers Manager) and make sure it is enabled.

---

### Post by oiio on 2008-06-14
it was the last thing.
thx alot

now he doesn't wnna connect but I'll first try figuring out that myself

it's enabled so i'm happy :)

---

