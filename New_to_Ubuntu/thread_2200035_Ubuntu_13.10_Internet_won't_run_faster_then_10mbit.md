---
title: "Ubuntu 13.10 Internet won't run faster then 10mbit."
date: 2014-01-17
forum: New to Ubuntu
---

### Post by chehus2 on 2014-01-17
Hello everyone.

I've been using qBittorrent when I noticed that the internet won't go faster than 10mb/s. I have a 100mb/s connection to the router and a 50/20mb internet speed. The same applies to my wireless connection. It's a 150mb/s wireless. Only works with the speed of 10mb/s.
My friend said that I could have the wrong drivers, but I don't think that's the problem. I've tried using speedtest.net to confirm that internet only runs with 10/10mb/s speed.

  *-network DISABLED      
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 78:dd:08:d2:ce:90
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.11.0-15-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:f4a00000-f4a0ffff
  *-network
       description: Ethernet interface
       product: Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB]
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 11
       serial: 54:42:49:5b:cf:e8
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full ip=192.168.2.3 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:41 memory:f2220000-f2223fff ioport:a000(size=256) memory:f2200000-f221ffff

Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: No
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: Unknown
Cannot get wake-on-lan settings: Operation not permitted
	Current message level: 0x000000ff (255)
			       drv probe link timer ifdown ifup rx_err tx_err
	Link detected: yes



Hope this information will help. Meanwhile I will check my router settings, to see if anything's wrong there. But I haven't touched the router for a while and it all worked well on my Windows PC.

---

### Post by chehus2 on 2014-01-17
Nevermind, it actually was a router problem.

---

