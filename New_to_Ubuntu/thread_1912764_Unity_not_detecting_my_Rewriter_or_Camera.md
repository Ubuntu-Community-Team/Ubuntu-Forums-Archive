---
title: "Unity not detecting my Rewriter or Camera"
date: 2012-01-21
forum: New to Ubuntu
---

### Post by Peterfc on 2012-01-21
Hi Guys

I have just connected my Usb Rewriter and a Fuji camera to my laptop. Normally they just get connected in the Unity bar at the side of the screen. For some reason nothing nothing has shown up on my screen. 

Thanks for reading my question

Advent laptop 3gb ram 250mb Hard drive Celeron 743 1.3Ghz 

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b197 Chicony Electronics Co., Ltd 
Bus 006 Device 002: ID 413c:3200 Dell Computer Corp. Mouse
Bus 006 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)

---

### Post by anewguy on 2012-01-21
Try prefacing the lsusb with sudo:

sudo lsusb


*IF* they show up then it might be something to do with udev usb default mounting rules.


Dave ;)

---

