---
title: "No Wireless"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by AcademyKP03 on 2008-05-08
I finally got to install Xubuntu - I had to use the ALT CD; and it boots up fine.

When I was installing Xubuntu on the ALT CD; there was something about how the network configuration couldn't be setup correctly .. I tried to select the autoconfigure option ... but kept failing ... anyways, skipped the autoconfiguration and went on to install it on the laptop ...

Here my problem ... I can't get ANY wireless connection even though, on XP - it was able to pickup all sorts of signals (we live in an apartment with lots of wireless, some protected and some not).  

Please help!

Thanks!

John

---

### Post by tamoneya on 2008-05-08
what do you get when you type ```
ifconfig
``` into terminal.

---

### Post by AcademyKP03 on 2008-05-08
> **tamoneya said:**
> what do you get when you type ```
ifconfig
``` into terminal.

eth0      Link encap:Ethernet  HWaddr 00:0f:1f:19:85:3d 
          inet addr:76.186.115.74  Bcast:255.255.255.255  Mask:255.255.252.0
          inet6 addr: fe80::20f:1fff:fe19:853d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:88435 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19639 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:42722649 (40.7 MB)  TX bytes:1614761 (1.5 MB)
          Interrupt:7

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:8908 (8.6 KB)  TX bytes:8908 (8.6 KB)

---

### Post by ugm6hr on 2008-05-08
Do you have a USB or PCI / internal wifi card?

Also: useful info in
```
lshw -C network
```

---

### Post by AcademyKP03 on 2008-05-08
> **ugm6hr said:**
> Do you have a USB or PCI / internal wifi card?

Also: useful info in
```
lshw -C network
```

YES, it has internal Wifi card

here's what I got:

marne@marne:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0            
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:19:85:3d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=76.186.115.74 latency=32 module=ssb multicast=yes
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:96:bb:61:97
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by tamoneya on 2008-05-08
the part to look at is this:
```
*-network DISABLED
description: Wireless interface
physical id: 1
logical name: wlan0
serial: 00:90:96:bb:61:97
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
```
See if this fixes it```
sudo ifconfig wlan0 down
```

---

### Post by ugm6hr on 2008-05-08
> product: BCM4306 802.11b/g Wireless LAN Controller

You have a Broadcom BCM4306.

These are not the best wifi cards for Linux, but do work OK-ish.

You need to install the fwcutter software.

Make sure you are online (with ethernet), and then go to Hardware / Restricted Drivers in System menu.

---

### Post by AcademyKP03 on 2008-05-08
> **tamoneya said:**
> the part to look at is this:
```
*-network DISABLED
description: Wireless interface
physical id: 1
logical name: wlan0
serial: 00:90:96:bb:61:97
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
```
See if this fixes it```
sudo ifconfig wlan0 down
```

Yup; that worked!

The propietary drivers menu came up - click on enable - and then PRESTO! - found that it was picking up signals

Thanks! god bless

---

