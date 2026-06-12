---
title: "unable to open drivers"
date: 2012-11-19
forum: New to Ubuntu
---

### Post by keithpitts on 2012-11-19
this is what i get
keithpitts@ubuntu:~$ sudo lshw -C network
[sudo] password for keithpitts: 
  *-network               
       description: Wireless interface
       product: RTL8191SEvA Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 10
       serial: 1c:65:9d:3c:3f:21
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192se driverversion=3.5.0-18-generic firmware=N/A ip=192.168.1.102 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 ioport:3000(size=256) memory:93500000-93503fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 60:eb:69:3b:f2:a7
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:91410000-91410fff memory:91400000-9140ffff memory:91420000-9142ffff
i'm not using a PCI Card

---

### Post by nothingspecial on 2012-11-19
Duplicate of this

[http://ubuntuforums.org/showthread.php?t=2085943](http://ubuntuforums.org/showthread.php?t=2085943)

Closed.

---

