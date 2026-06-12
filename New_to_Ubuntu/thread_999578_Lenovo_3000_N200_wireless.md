---
title: "Lenovo 3000 N200 wireless"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by steinzeitmensch on 2008-12-02
Hi guys,
Was wondering if anyone out there could help me get the wireless working on my laptop.
it is a Lenovo 3000 N200 and this is the output from terminal on sudo lshw -C network

```
 *-network               
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=iwl3945 latency=0 module=iwl3945
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 02
       serial: 00:1b:38:0b:c6:01
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full ip=172.19.12.39 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s

```

But when I go into network settings and look at the wireless properties, the dialogue is greyed out and the enable roaming mode is checked. I gather that is the right setting if I do not know about any specific networks around me.

Where do I see the wireless networks to choose from? I know I have several around me but I cannot use them :(

---

### Post by montas on 2009-03-16
ok solved this, go to BIOS and restore defaults in the N200

after this the wireless light lit up and wireless worked

---

