---
title: "losing wireless connection"
date: 2012-09-08
forum: New to Ubuntu
---

### Post by dblackmon on 2012-09-08
Any help on how to diagnose what is wrong with my connection? I use a wireless router (linksys) and there are other computers connected to it, but there is no problem with them. I use ubuntu with the one that is have connectivity issues. Is there something on the command line I can use to figure out what is going on?

---

### Post by steeldriver on 2012-09-08
first thing would be to figure out exactly what card / chipset you have

if it's pci something like

```
lspci -nn | grep -E -e '\[0200\]' -e '\[0280\]'
```else if it's usb

```
lsusb
```

or you can use

```
lshw -C network
```

to list all the networking hardware

---

### Post by dblackmon on 2012-09-08
hi thanks- here is the output. not sure what to do next


 *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth2
       version: 01
       serial: 0c:60:76:50:15:5f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:57100000-57103fff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: 00:26:22:26:ff:d1
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:46 memory:55000000-5503ffff ioport:2000(size=128)

---

