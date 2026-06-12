---
title: "Driver Install of Ethernet Adapter DGE-530T"
date: 2015-08-26
forum: New to Ubuntu
---

### Post by a.whitwell on 2015-08-26
Hello,

I'm having trouble installing a D-Link DGE-530T hardware version D2 ethernet card adapter. It came with a disk with the drivers for a linux system, but I have no idea how to install the drivers from the disk or from the website. I know this is a super noob question, but I'll take any help. Xubuntu 14.04

---

### Post by Vladlenin5000 on 2015-08-26
Hi and welcome.

 D-Link DGE-530T is an old card based on some Marvell chipset which has native support since a long time ago therefore you shouldn't need to install any drivers.

---

### Post by cariboo on 2015-08-26
As Vladlenin5000 said, just plug the card in and start your computer, it should be auto-detected and the driver loaded. To check once the system has booted, open a terminal and type:

```
sudo lshw -C networtk
```

The results shoud look similar to this:

```
*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: enp1s0
       version: 07
       serial: f8:a9:63:7a:e4:e3
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8106e-1_0.0.1 06/29/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:89 ioport:e000(size=256) memory:d0804000-d0804fff memory:d0800000-d0803fff
```

---

### Post by a.whitwell on 2015-08-26
Thanks for the help! Turns out I just needed to reboot the computer. Feeling really stupid right about now.

---

