---
title: "no sign of wireless at all"
date: 2012-03-30
forum: New to Ubuntu
---

### Post by dreyyy07 on 2012-03-30
I have been trying to fix my wireless on my hp mini 210 since installed ubuntu, but now when i open the network manager i dont see any sign of wireless anymore, not even the 'enable wireless' line

---

### Post by Jake5 on 2012-03-30
Could you post the output of ```
sudo lshw -c Network
iwconfig
rfkill list all
```
Run the commands one line at a time, obviously. This should tell us what we need to know to help you.

---

### Post by Jake5 on 2012-03-30
Also, is there a physical WiFi on/off button on your machine?

---

### Post by tehchibipanda on 2012-03-30
I had the same problem. If you are using a broadcom chipset (Which I assume is the case...that's where the problems seem to lie mainly...) check out [http://ubuntuforums.org/showthread.php?t=1889170](http://ubuntuforums.org/showthread.php?t=1889170) as that was what helped me get it working.

---

### Post by dreyyy07 on 2012-04-04
-after sudo lshw -c Network
*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 04
       serial: 68:b5:99:d3:a2:bb
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:50004000-50004fff memory:50000000-50003fff
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
       resources: memory:52000000-5200ffff
-after iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ppp0      no wireless extensions.

-after rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

---

### Post by dreyyy07 on 2012-04-04
i have a physical WiFi on/off button

---

### Post by roger_1960 on 2012-04-04
Hi

Assuming the on/off wasn't the problem, which version of ubuntu do you have installed?  Have a look at this post:
[http://ubuntuforums.org/showthread.php?t=1669283&highlight=RT3090](http://ubuntuforums.org/showthread.php?t=1669283&highlight=RT3090)

---

### Post by dreyyy07 on 2012-04-04
ubuntu 11.04

---

