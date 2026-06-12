---
title: "WiFi Issues"
date: 2012-03-03
forum: New to Ubuntu
---

### Post by DrPcG on 2012-03-03
I've used Ubuntu before, but stopped for awhile because the netbook broke. I now have installed it on this desktop, but the wireless will not work. My wireless device is Lynksys, and it is hooked up to the UBS Extension Base that it came with. It works perfectly fine on the Vista OS (what I'm using to post this). If anyone knows how to fix this, I'd be quite happy. I've been on this for a few hours.

Thanks!

---

### Post by nothingspecial on 2012-03-03
Well you need you give a little info.

Press Ctrl-Alt-T and when the terminal opens type

```
sudo lshw -C network
```

Post the output back here.

---

### Post by DrPcG on 2012-03-03
*-network
description: Ethernet interface

product: PRO/100 VE Network Connection
vendor: Intel Corporation
physical id: 8
bus info: pci@0000:06:08.0

logical name: eth0

version: 01

serial: 00:19:d1:33:43:37
size: 10Mbit/s
capacity: 100Mbit/s

width: 32 bits
clock: 33MHz

capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s

resources: irq:20 memory:50000000-50000fff ioport:1100(size=64)

---

### Post by DrPcG on 2012-03-03
I didn't think about asking, that is what you wanted right? Or did I miss something?

---

### Post by DrPcG on 2012-03-03
*Bump* Help please? I really have been at this for a few hours, switching between two OS's to post problems is getting annoying.

---

### Post by DrPcG on 2012-03-03
I would really love some help. Been browsing looking for answers. So far? Nothing.

---

### Post by nd456 on 2012-03-03
Model of the NIC? (more info than just "linksys") and what version of ubuntu?

---

### Post by kurt18947 on 2012-03-03
> **DrPcG said:**
> I would really love some help. Been browsing looking for answers. So far? Nothing.

You're posting info on your wired (ethernet).  If your WiFi adapter isn't recognized, it won't show up.  If the WiFi adapter is USB, the command "lsusb" will show the chipset which is what is really needed.  If the wifi adapter is internal, "lspci" will do the same.  We're looking for something that looks like this:

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0409:0058 NEC Corp. HighSpeed Hub
**Bus 002 Device 002: ID 0846:9030 NetGear, Inc. WNA1100 Wireless-N 150 [Atheros AR9271]**
Bus 004 Device 002: ID 047d:2048 Kensington 
Bus 004 Device 003: ID 413c:1002 Dell Computer Corp. Keyboard Hub
Bus 001 Device 005: ID 04f9:01f3 Brother Industries, Ltd 
Bus 004 Device 004: ID 413c:2002 Dell Computer Corp. SK-8125 Keyboard

```

---

