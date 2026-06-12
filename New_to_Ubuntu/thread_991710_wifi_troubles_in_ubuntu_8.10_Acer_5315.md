---
title: "wifi troubles in ubuntu 8.10 Acer 5315"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by lapubell on 2008-11-24
Hello out there.  I'm working on getting the wifi for a buddy's laptop to work.

I've tried a few things, but don't really know how this usually goes (trouble shooting hardware, I usually buy smart and get what I know will work with Linux...).  Please help me out by shooting me in the right direction, and I can use the terminal and can also compile things.  :)

Here is the first thing that I'm sure you will all want to see:

user@laptop:~$ lspci | grep ethernet
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

Does this mean that I need to get the broadcom device working, or the Atheros one?  When I am in a place with wired internet, that device works, but no wifi device is active...

please help?

---

### Post by grazed on 2008-11-24
try installing this package from synaptic. it seems to help most users with the atheros issues.

linux-backports-modules-intrepid

---

### Post by lapubell on 2008-11-24
wow.  i had no idea that package existed.  you just saved me lots of forum reading.

cheers!

---

