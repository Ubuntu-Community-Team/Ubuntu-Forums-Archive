---
title: "setting up wireless on my laptop"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by Dave B on 2008-08-28
HI 

Im having problems setting up my wireless connection on my laptop running XUBUNTU with a Linksys wpc54G V3 wireless card.  can someone plese help guide me?

Thanks 

DAVE

---

### Post by Crafty Kisses on 2008-08-28
Post the results of this command:
```
lshw -C network
```

---

### Post by Dave B on 2008-08-29
um gunna go back to regular Ubuntu HH then try the wireless network  I just dont like xubuntu as much

---

### Post by Dave B on 2008-08-29
HI Codename

> **Codename said:**
> Post the results of this command:
```
lshw -C network
```

Here are the results:

dave@lappy:~$ sudo lshw -C network
[sudo] password for dave: 
  *-network               
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:06:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:18:f8:d4:c4:87
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
dave@lappy:~$ 



Thank you

---

