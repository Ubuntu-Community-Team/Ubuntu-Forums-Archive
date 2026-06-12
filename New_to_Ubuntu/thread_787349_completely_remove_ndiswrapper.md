---
title: "completely remove ndiswrapper?"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by fontenot_1031 on 2008-05-08
Well as usual I completely screwed up ndiswrapper.  I'm using Debian Etch right now and originally I installed ndiswrapper through apt-get only to find out that on debian you need to build it from source.  I built it correctly but completely screwed it up because it is still using bcm43xx (no WEP support on that open source driver).  I have been following this tutorial []() and has been working fairly well.  Here is my current lshw -C network
```
  *-network:0 DISABLED
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@06:02.0
       logical name: eth0
       version: 02
       serial: 00:14:a5:77:19:da
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.18-6-486 la tency=64 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:c0200000-c0201fff irq:225
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@06:06.0
       logical name: eth1
       version: 10
       serial: 00:16:d4:03:af:fd
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 1 00bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driververs ion=0.9.27 duplex=full ip=192.168.1.3 latency=128 link=yes maxlatency=64 mingnt= 32 multicast=yes port=MII speed=100MB/s
       resources: ioport:a000-a0ff iomemory:c0202000-c02020ff irq:217
```
If you know how to completely remove ndiswrapper (still shows up when I type 'ndiswrapper' into xterm and apt-get remove ndiswrapper or apt-get remove ndiswrapper-utils has not proved sucessful).  Even if I may be close to having the driver completely installed I would much rather have it completely removed so that I can install it fresh again (it would ease my OCD mind).
By the way I have had success with this tutorial on Ubuntu Hardy but would prefer to use Etch.

---

