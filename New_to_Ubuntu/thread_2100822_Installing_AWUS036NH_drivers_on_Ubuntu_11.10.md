---
title: "Installing AWUS036NH drivers on Ubuntu 11.10"
date: 2013-01-02
forum: New to Ubuntu
---

### Post by ACagliano on 2013-01-02
I searched on this forum for a procedure to install the driver for the listed antenna on Ubuntu 11.10. It produced a few warnings during "make", but installed without issue. I rebooted, then ran this command:

sudo lshw -C network

And this was the output... 
my two listed devices were:

BCM4322 802.11a/b/g/n Wireless LAN controller  (eth1)
and
NetXtreme BCM5764M Gigabit Ethernet PCIe (ra0)

are one of these the device? What else can I do?

---

