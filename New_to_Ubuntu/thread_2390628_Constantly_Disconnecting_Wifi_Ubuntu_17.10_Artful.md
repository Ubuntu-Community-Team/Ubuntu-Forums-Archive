---
title: "Constantly Disconnecting Wifi Ubuntu 17.10 Artful"
date: 2018-04-30
forum: New to Ubuntu
---

### Post by holsten on 2018-04-30
Hi there,
I'm very new to Linux so please bare with me!<br><br>

After initially installing Ubuntu my wifi worked fine for ages. I'd installed a VPN (PIA) and it worked fine initially. However,&nbsp; perhaps because of an upgrade a while back, I am now unable to connect to my wifi without going via the VPN (I have checked the killswitch is off in the VPN settings). 

More frustratingly, the wifi continuously disconnects - I'm lucky if I get 10 mins uninterrupted service atm. I've tried changing the power management settings as some have suggested, but although this appeared to help initially, it doesn't seem to anymore. I also found that running the update && upgrade in the terminal would sometimes fix it, but now it is just as bad as before and I am fully up to date.

Below is the output from lshw -class network, if that helps to get started with

  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.1
       bus info: pci@0000:02:00.1
       logical name: enp2s0f1
       version: 12
       serial: 80:fa:5b:45:68:af
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8411-2_0.0.1 07/08/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:125 ioport:e000(size=256) memory:df114000-df114fff memory:df110000-df113fff
  *-network
       description: Wireless interface
       product: Wireless 8265 / 8275
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 78
       serial: 00:28:f8:ba:c7:28
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.13.0-39-generic firmware=31.560484.0 ip=192.168.1.68 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:128 memory:df000000-df001fff
  *-network:0
       description: Ethernet interface
       physical id: 1
       logical name: docker0
       serial: 02:42:5d:d5:ec:4d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=172.17.0.1 link=no multicast=yes
  *-network:1
       description: Ethernet interface
       physical id: 2
       logical name: br-15ce41b9ab57
       serial: 02:42:98:ac:3f:d1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=172.18.0.1 link=no multicast=yes

Many thanks in advance for any help!

---

