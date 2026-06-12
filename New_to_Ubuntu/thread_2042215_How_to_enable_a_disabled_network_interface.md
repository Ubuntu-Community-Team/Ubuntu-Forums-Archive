---
title: "How to enable a disabled network interface?"
date: 2012-08-14
forum: New to Ubuntu
---

### Post by Guruprasad on 2012-08-14
guruprasad@BC2:~$ sudo lshw -class network
*-network
description: Ethernet interface
product: RTL8111/8168B PCI Express Gigabit Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: 06
serial: bc:ae:c5:6d:bb:52
size: 100MB/s
capacity: 1GB/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=116.68.73.147 latency=0 link=yes multicast=yes port=MII speed=100MB/s
resources: irq:41 ioport:d800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff
*-network [COLOR="Red"]**DISABLED**[/COLOR]
description: Ethernet interface
product: RTL-8139/8139C/8139C+
vendor: Realtek Semiconductor Co., Ltd.
physical id: 5
bus info: pci@0000:03:05.0
logical name: eth1
version: 10
serial: ff:ff:ff:ff:ff:ff
size: 100MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
resources: irq:20 ioport:e800(size=256) memory:febffc00-febffcff memory:febe0000-febeffff

---

### Post by Finnicella on 2012-08-14
Hi, I'm not very expert, but you can try to see if there are some blocks with this command:
```
sudo rfkill list all
```
if there are, give this command:
```
sudo rfkill unblock all
```
If that I wrote doesn't work try with:
```
sudo ifconfig eth1 down
```
and
```
sudo ifconfig eth1 up
```
Bye and sorry for my english.:D

---

