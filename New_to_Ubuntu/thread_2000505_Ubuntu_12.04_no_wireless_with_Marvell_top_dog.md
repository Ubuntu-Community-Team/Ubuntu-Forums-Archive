---
title: "Ubuntu 12.04 no wireless with Marvell top dog"
date: 2012-06-09
forum: New to Ubuntu
---

### Post by AlaskanPotHead on 2012-06-09
I've installed Ubuntu 12.04 on my wifes Gateway MT6458. It has the Marvell top dog wireless but I can't get it to work. I've searched these forums for 2 days now and I'm out of ideas. Can anyone help me get it working, please? Here is the output for sudo lshw -C network:

sudo lshw -C network
[sudo] password for succubus: 
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:e0:b8:d4:35:6b
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full firmware=N/A ip=192.168.1.112 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 memory:c0200000-c0203fff ioport:a000(size=256)
  *-network UNCLAIMED
       description: Ethernet controller
       product: 88W8362e [TopDog] 802.11a/b/g/n Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:c0310000-c031ffff memory:c0300000-c030ffff

---

### Post by AlaskanPotHead on 2012-06-09
Never mind. Just found out (on a different site) that you cannot get this working on a 64 bit OS. Guess it's time to put a 32 bit version of Ubuntu on my laptop. :(

---

