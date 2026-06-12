---
title: "Particular Wifi not detecting"
date: 2015-05-29
forum: New to Ubuntu
---

### Post by anug on 2015-05-29
Hi All,
I am using Ubuntu 14.04 OS in Dell Vostro 2520. I am quite new to this OS. I have my wifi enabled but my home network is not listed in available list. My wifi is WPA only enabled. I have the drivers installed. I am able to connect to the same wifi network from phones and Windows. What other settings should I check to resolve the problem? Please help.

```

*-network               
       description: Wireless interface
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 9c:2a:70:d9:d8:05
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.248 (r487574) latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:19 memory:f7c00000-f7c07fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 07
       serial: e0:db:55:ad:ce:63
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.1.34 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:40 ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff

```

---

### Post by cariboo on 2015-05-29
Your post is a little sparse on details, could you open a terminal and run the following command:

```
sudo lshw -C network
```

and paste the output in your next post.

the output should look similar to this:

```
sudo lshw -C network
[sudo] password for cariboo: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 07
       serial: f8:a9:63:7a:e4:e3
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8106e-1_0.0.1 06/29/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:89 ioport:e000(size=256) memory:d0804000-d0804fff memory:d0800000-d0803fff
  *-network
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: b8:ee:65:8a:1b:f7
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.19.0-18-generic firmware=N/A ip=192.168.0.106 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d0700000-d077ffff memory:d0780000-d078ffff
```

---

### Post by anug on 2015-05-29
Added the output in my original post.

---

### Post by ajgreeny on 2015-05-29
Have a good look at the sticky post about that wifi card at [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

Come back again if that doesn't help.

---

### Post by wildmanne39 on 2015-05-29
If you still need help after reviewing the link posted above please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

