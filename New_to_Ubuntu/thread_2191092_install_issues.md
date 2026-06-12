---
title: "install issues"
date: 2013-11-30
forum: New to Ubuntu
---

### Post by dkeach on 2013-11-30
I have installed Ubuntu 10.04 on a dell latitude e6410.  I have no network connection whatsoever.  I have read many forum posts and attempted to correct this to no avail.  Could someone walk me through troubleshooting and correcting this issue.  I only know enough about Linux to be dangerous.  Thanks in advance.

---

### Post by newb85 on 2013-11-30
Welcome to Ubuntu and the forums. 

First, you should know that unless you only installed the server edition (No GUI), 10.04 is no longer supported, and thus not a good idea to run. 
You should stick with something supported,  like 12.04 or 13.10.

Help is much easier when more is known about your card.  A good start:
```
 sudo lshw -C network 
```

More than likely, a moderator will move this to the networking forum, and Wildman will be able to get you up and running.

---

### Post by dkeach on 2013-12-01
> **newb85 said:**
> Welcome to Ubuntu and the forums. 

First, you should know that unless you only installed the server edition (No GUI), 10.04 is no longer supported, and thus not a good idea to run. 
You should stick with something supported,  like 12.04 or 13.10.

Help is much easier when more is known about your card.  A good start:
```
 sudo lshw -C network 
```

More than likely, a moderator will move this to the networking forum, and Wildman will be able to get you up and running.

Unfortunately I need to run 10.04 because I am using linuxCNC which is only compatible up to 10.04.  I attempted to upgrade another machine and totally lost the ability to use LinuxCNC.

When I run lshw - C network i recieve the following:
  *-network              
       description: Ethernet interface
       product: 82577LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 05
       serial: 00:26:b9:d1:3b:2d
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=0.12-1 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:f6900000-f691ffff memory:f6980000-f6980fff ioport:7040(size=32)
  *-network UNCLAIMED
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f4100000-f4103fff

 Thanks for your help

---

