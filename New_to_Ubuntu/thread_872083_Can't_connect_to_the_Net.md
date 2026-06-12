---
title: "Can't connect to the Net"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by L0rdMathias on 2008-07-27
Ok, I have a Toshiba Satellite laptop that i'm running Vista and Ubuntu 8.04 on, and only in Ubuntu i can't connect to the internet.

I've read some other posts to try and fix it myself, but i can't seem to do that. The Realtek Wireless card that came on the Computer is recognized by Ubuntu, but i can't find or connect to any network
this is my sudo lshw -C network command result in terminal:
*-network DISABLED
description: Ethernet interface
       
product: RTL8101E PCI Express Fast Ethernet controller
       
vendor: Realtek Semiconductor Co., Ltd.
       
physical id: 0
       
bus info: pci@0000:08:00.0
       
logical name: eth0
       
version: 01
       
serial: 00:a0:d1:8a:b1:10
       
capacity: 1GB/s
       
width: 64 bits
       
clock: 33MHz
       
capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair

It may just be me but the big DISABLED might be the problem


If it matters i have an AMD 64 processor.

---

### Post by jamesrfla on 2008-07-27
Could you provide the laptop model? Also type this into the terminal ```
ifconfig
```
Are you having trouble connecting to the wireless network?

---

### Post by L0rdMathias on 2008-07-27
It is a Satellite A215-S7437 
and yes, it is the wireless i'm having trouble with
and here are the results::

lo     Link encap:Local Loopback
 inet addr:127.0.0.1 Mask:255.0.0.0
 inet6 addr: ::1/128 Scope:Host
 UP LOOPBACK RUNNING MTU:16436 Metric:1
 RX packets:484 errors:0 dropped:0 overruns:0 frame:0
 TX packets:484 errors:0 dropped:0 overruns:0 carrier:0   
 collisions:0 txqueuelen:0
 RX bytes:39204 (38.2 KB) TX bytes:39204 (38.2 KB)

I tried this yesterday, and had an eth0 entry also instead of just lo, so i wonder if i accidentally deleted that somehow (wireless internet still didn't work yesterday when i installed Ubuntu)

---

### Post by L0rdMathias on 2008-08-01
OK, disregard this, i had to reinstall vista on my computer, and that reset the partitions, which means that i had to reinstall Ubuntu, but i still am having trouble with wireless network connection

---

