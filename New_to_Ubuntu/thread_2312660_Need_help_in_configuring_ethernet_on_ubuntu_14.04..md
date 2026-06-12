---
title: "Need help in configuring ethernet on ubuntu 14.04. LTS"
date: 2016-02-06
forum: New to Ubuntu
---

### Post by zvor on 2016-02-06
Hi all,

I have recently bought a new laptop and have installed Ubuntu 14.04 LTS, now I have trouble configuring my ethernet connection. The ethernet worked fine on my previous computer running Ubuntu 12.04 LTS. Now I cannot get it to work.

The output of lshw gives the following:

  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 14:dd:a9:23:99:ea
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-3_0.0.1 04/23/13 ip=100.74.213.168 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:48 ioport:e000(size=256) memory:f7204000-f7204fff memory:f7200000-f7203fff
  *-network
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 28:c2:dd:35:14:8b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.19.0-25-generic firmware=N/A ip=172.20.10.4 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:f7100000-f717ffff memory:f7180000-f718ffff

Could someone please assist me on this? I apologize in advance, but I am not very knowledgeable on ubuntu, so I might ask for clarification to things that might seem obvious.

Thanks for any information!

---

### Post by grahammechanical on 2016-02-06
Please explain what you mean by "cannot get it to work." 

There are drivers for both wired (ethernet) and wireless adapters.

Ethernet adapter

> broadcast=yes _driver=r8169 driverversion=2.3LK-NAPI_ duplex=full  firmware=rtl8168g-3_0.0.1 04/23/13 ip=100.74.213.168 latency=0 link=yes  multicast=yes port=MII speed=1Gbit/s

Wireless adapter

> broadcast=yes _driver=ath9k driverversion=3.19.0-25-generic_ firmware=N/A  ip=172.20.10.4 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn

The printout for both adapters the printout says "broadcast=yes." That means that the adapters are powered on and the drivers are working. Both adapters are broadcasting there existence. The ethernet adapter has a connection speed of 1Gbit/s. 

Do you see a Network Manager icon in the top panel? It will be 2 arrows going in opposite directions. Click on the icon and in the drop down menu confirm that Networking is enabled. That same menu should also list the ethernet adapter. Does it say disconnected? An ethernet adapter that is connected will have an option to disconnect in that menu. What do you see?

Regards.

---

### Post by ajgreeny on 2016-02-06
What is the output of the terminal command ```
ifconfig
```  That may give us some clues.
I have the same ethernet controller in my desktop machine which has always worked fine.

I see you also have a wifi adapter; does that work?

---

