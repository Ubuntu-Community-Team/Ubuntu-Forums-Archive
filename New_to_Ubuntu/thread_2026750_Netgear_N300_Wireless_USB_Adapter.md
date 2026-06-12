---
title: "Netgear N300 Wireless USB Adapter"
date: 2012-07-15
forum: New to Ubuntu
---

### Post by GCSTider on 2012-07-15
How do you install Netgear N300 Wireless USB Adapter on a Dell Latitude D830?

---

### Post by anewguy on 2012-07-15
With device plugged in, open a terminal window and type

lsusb

This will give us the device manufactur and device id, via the "xxxx:xxxx" for the device.

Just copy that output back here in a post.

---

### Post by GCSTider on 2012-07-16
Sorry for the delay. Just got off of work. Here is the lsusb from the terminal window.

donna@donna-Latitude-D830:~$ lsusb
Bus 007 Device 003: ID 0b97:7772 O2 Micro, Inc. OZ776 CCID Smartcard Reader
Bus 007 Device 002: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 0846:9020 NetGear, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
donna@donna-Latitude-D830:~$

---

