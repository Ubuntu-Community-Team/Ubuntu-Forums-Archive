---
title: "Wireless Often Not Available on Startup; Available after shutdown/start/shutdown etc"
date: 2014-02-26
forum: New to Ubuntu
---

### Post by flunewname on 2014-02-26
The problem I have is that now I have a wireless connection, but when I shutdown my computer, I might not have any internet connections show for the next ten startups, then, magically, on the eleventh or twentyith startup it will work.  Can't find a pattern to why or why not.

Super newbie using LTS

```

rebecca@rebecca-MM061:~$ sudo lshw -c network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:efdfc000-efdfffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:0a:91:64
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:17 memory:ef9fe000-ef9fffff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1d:d9:5f:f8:85
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.5.0-46-generic firmware=508.1084 ip=192.168.1.19 link=yes multicast=yes wireless=IEEE 802.11bg

```

---

### Post by ian-weisser on 2014-02-26
Look in /var/log/dmesg or /var/log/syslog for error messages.
Software failures usually result in error messages.

If there are not any error messages, then start looking at your hardware.

---

