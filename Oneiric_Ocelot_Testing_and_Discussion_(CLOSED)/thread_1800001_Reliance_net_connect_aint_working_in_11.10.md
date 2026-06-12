---
title: "Reliance net connect aint working in 11.10"
date: 2011-07-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by kanishkdudeja on 2011-07-08
I configured the network connection for Reliance Netconnect data card in the exact same way as i did in 11.04..

but its not getting connected in 11.10..

any suggestions as to how to get it working?

---

### Post by kanishkdudeja on 2011-07-10
bump.

---

### Post by cariboo on 2011-07-10
Could you paste the output of:

```
sudo lshw -C network
```

and:

```
lsusb
```

in your next post.

---

### Post by kanishkdudeja on 2011-07-10
```
kanishk@kanishk-Inspiron-1525:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 19d2:fff1 ONDA Communication S.p.A. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```
kanishk@kanishk-Inspiron-1525:~$ sudo lshw -c network
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:d1:4a:ab
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:fe8fc000-fe8fffff ioport:de00(size=256)
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:1f:e1:ce:37:65
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:fe7fc000-fe7fffff
```

In the first output, i think, ONDA Communication S.p.A. is my data card.
But the second output only shows the ethernet card and the wireless card. It does not show the data card.

These are the same outputs i get in 11.04..in that it gets connected.

---

### Post by kanishkdudeja on 2011-10-01
bump.

---

### Post by cariboo on 2011-10-01
Is this device an add in card, or a usb device? You say it shows in lsusb, but at the same time you call it a card. Could you plug your device in, if it is usb, then open a terminal and type:

```
dmesg | tail -n15
```

and paste the output in your next post.

---

### Post by professor76 on 2011-10-01
Output of 

ls /dev/ttyU* 

would be helpful as well.

---

