---
title: "wireless conectivity problem"
date: 2012-12-20
forum: New to Ubuntu
---

### Post by bawasingh on 2012-12-20
Sir ,
      i am recently installed ubuntu 12.04 LTS . i can't set up wireless connection . on the top of desktop screen there is wired connectivity but no search for my wireless network pl help me to solve my problem.........

---

### Post by DuckHook on 2012-12-20
Many are happy to help, but impossible to solve problem without info. Please see [this]("http://ubuntuforums.org/showthread.php?t=1422475") sticky.

---

### Post by bawasingh on 2012-12-20
amankpanwar@amankpanwar-HCL-Notebook:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0500000-f050ffff
  *-network
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: 70:71:bc:44:98:e3
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.0.100 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:46 memory:f0400000-f043ffff ioport:d000(size=128)

---

