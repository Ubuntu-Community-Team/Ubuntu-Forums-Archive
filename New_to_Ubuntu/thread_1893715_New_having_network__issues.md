---
title: "New having network  issues"
date: 2011-12-10
forum: New to Ubuntu
---

### Post by Rhino22 on 2011-12-10
I'm completely new, and almost on the verge of burning my computer.
 
I installed ubuntu server 11.04 on a new computer
 
Network is not working.
 
lshw -C network
 
both ethernet and wireless interfaces are disabled!? try pinging stuff no response. cant use apt-get.

---

### Post by papibe on 2011-12-10
Could you post the result of the same command, but using sudo?
```
sudo lshw -C network
```
That way we can see what NICs you have.

Regards.

---

### Post by Rhino22 on 2011-12-10
is there anyway i can actually copy it? i hate having to type it out:
 
[43.35722] CPU0: Core temp above threshold, cpu clock throttled
 " "             CPU1   " "
 
*-network:0 DISABLED
description: Ethernet interface
productL RTL-8139/8139C/8139C+
vendor: Realtek semiconductor Co., Ltd.
physical id: 2
bus info: [EMAIL="pci@0000:02:02.0"]pci@0000:02:02.0[/EMAIL]
logical name: eth0
version: 10
serial 00:16:76:47:19:a9
size 100Mbit/s
capacity: 100Mbit/s
width 32 vuts
clock 33MHz
capabilities pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configurationL autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=64 link=no max latency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
 
resources irq:21 ioport:de00(size=256) memory:fddff000-fddff0ff
*-network:1 DISABLED
description: wireless interface
product: RT2561/RT61 802.11g PCI
vendor: Ralink corp.
physical id: 4
bus info: [EMAIL="pci@0000:02:04.0"]pci@0000:02:04.0[/EMAIL]
logical name: wlan0
version: 00
serial:00:11:50:dd:b6:a5
width: 32 bits
clock 33MHz
capabilities: pm bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=rt61pci driverversion=2.6.38-8-server firmware=N/A latency=64 link=no multicast=yes wireless=IEEE 802..11bg
resources: irq:17 memory fddf0000-fddf7fff
 
no idea whats going on. before i reinstalled it was ok. now i reinstall again same issue pops up. really annoying there isnt much info out there to help

---

### Post by papibe on 2011-12-10
Try this to get you ethernet card working:
```
sudo mii-tool eth0 -F 10baseT-FD
sudo rmmod 8139too
sudo modprobe 8139too
```
After that check your card's status by running:
```
ifconfig
```
Hope it helps.
Regards.

BTW, in case you still don't have network, I think it could be easier to redirect the outputs to a file, and copy it into a USB stick (instead of typing them manually).

---

