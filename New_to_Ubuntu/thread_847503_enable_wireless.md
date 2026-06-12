---
title: "enable wireless"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by gaddo on 2008-07-02
Hi can someone help with enabling my wireless card. I am running 8.04 this a bit strange because it just worked in previous versions?
The output of sudo lshw -C network follows

 *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:15:e6:23
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.81 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network:1 DISABLED
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:06:02.0
       logical name: wifi0
       version: 01
       serial: 00:16:ce:8a:89:c9
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11b

Any help would be great

---

### Post by pofigster on 2008-07-09
Are you using ndiswrapper or what?  How did you install the drivers?

---

### Post by mikewhatever on 2008-07-09
It seems to be enabled as far as the driver goes. Why do you think it isn't?

---

### Post by gaddo on 2008-07-20
> **pofigster said:**
> Are you using ndiswrapper or what?  How did you install the drivers?

No not using ndiswrapper as for the drivers didnt install them just installed 8.04 and it did it.

Gaddo

---

### Post by gaddo on 2008-07-20
> **mikewhatever said:**
> It seems to be enabled as far as the driver goes. Why do you think it isn't?
I saw this (*-network:1 DISABLED) in the output of udo lshw -C network!

---

### Post by noimus on 2008-07-24
holy **** i have the same thing!

> *-network:0
description: Ethernet interface
product: RTL-8139/8139C/8139C+
vendor: Realtek Semiconductor Co., Ltd.
physical id: 1
bus info: pci@0000:06:01.0
logical name: eth0
version: 10
serial: 00:16:d4:15:e6:23
size: 100MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.81 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
[B]
BUT I DONT GET[/B] Could it be because i didnt install Ubuntu yet? How do i get wireless up and running?


*-network:1 DISABLED
description: Wireless interface
product: AR2413 802.11bg NIC
vendor: Atheros Communications Inc.
physical id: 2
bus info: pci@0000:06:02.0
logical name: wifi0
version: 01
serial: 00:16:ce:8a:89:c9
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11b

---

### Post by DapperMe17 on 2008-07-24
That isn't an easy chip to get working out-of-the-box. Makes no difference if LiveCD or installed.

The good news...yes, you can get it to work, with some work. If you have a temporary wired connection, you'll be in business.

Do a "How To:" search for that wireless chip & the details will be there.

---

