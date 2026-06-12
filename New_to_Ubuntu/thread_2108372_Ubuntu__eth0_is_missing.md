---
title: "Ubuntu : eth0 is missing"
date: 2013-01-24
forum: New to Ubuntu
---

### Post by guyafe on 2013-01-24
Hi,
I have just installed Ubuntu 12.10 on a brand new desktop, and found out that the OS can't detect eth0 nor connect to wired network.
I was able to connect perfectly using wireless PCI card.
Running hwinfo did show that the interface exist and suppose to be working.
I have an onboard netowrk interface on a Gigabyte H77-D3H motherboard.
Googling out showed me two possible solutions:
The first was to manually enter eth0 record in /etc/network/interfaces but that only caused the computer to crash, and not being able to restart at all (only in some kind of safe mode). After plating it a bit more, it caused the OS to always start with an ambigous error message, so I have finally reinstalled Ubuntu but the problem reoccured.

The second solution was to adjust some records in Udev but I was too afraid of doing this before consulting here.

Thanks for your reply,
Guy

---

### Post by Nr90 on 2013-01-24
What does
sudo lshw -class network
show?

---

### Post by guyafe on 2013-01-24
It shows that the controller exists:
```
guy@Guy-Comp:~$ sudo lshw -class network
  *-network               
       description: Wireless interface
       product: RT3060 Wireless 802.11n 1T/1R
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 80:1f:02:2e:ee:38
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.5.0-17-generic firmware=0.34 ip=10.100.101.105 latency=32 link=yes maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f7e00000-f7e0ffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR8161 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list
       configuration: latency=0
       resources: memory:f7d00000-f7d3ffff ioport:e000(size=128)
```

---

### Post by sandyd on 2013-01-24
The card is a bit new - drivers not in Ubuntu yet.
see [http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller](http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller) for instructions ;)

---

### Post by guyafe on 2013-01-25
Great!
That is exactly what I was looking for.
Still, I think that for now I'll stay with the wireless card because I too newbie to handle beta drivers.

Guy

---

