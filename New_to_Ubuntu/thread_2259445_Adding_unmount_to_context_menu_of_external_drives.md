---
title: "Adding unmount to context menu of external drives"
date: 2015-01-04
forum: New to Ubuntu
---

### Post by mkoniecz on 2015-01-04
I want to safely remove external HDD and pendrive without using 'Disks' utility from 'Preferences' (it is much less convenient and to make it worse - it likes to crash).

I found [http://askubuntu.com/questions/98784/safely-unmount-external-drive-on-lubuntu](http://askubuntu.com/questions/98784/safely-unmount-external-drive-on-lubuntu) as an alternative, but I would prefer to have access directly from context menu.

---

### Post by Dennis N on 2015-01-04
This is Lubuntu?  This command might work but I haven't tested it yet (you can):
If the drive is sdb, try:
```
sudo udisksctl power-off --block-device /dev/sdb
```
description from the man page:
> 
udisksctl power-off {--object-path OBJECT | --block-device DEVICE}
                 [--no-user-interaction]

power-off
           Arranges for the drive to be safely removed and powered off. On the
           OS side this includes ensuring that no process is using the drive,
           then requesting that in-flight buffers and caches are committed to
           stable storage. The exact steps for powering off the drive depends
           on the drive itself and the interconnect used. For drives connected
           through USB, the effect is that the USB device will be deconfigured
           followed by disabling the upstream hub port it is connected to.
If it works, incorporating it into the right-click options is another matter. That will require some research. Possibly it could also be a little script started from a desktop icon. Interesting - I plan to look into it.

---

### Post by Dennis N on 2015-01-04
Just to add: You title says "Add unmount..."
If unmount is what you want, you can change **power-off** to **unmount**

---

### Post by Dennis N on 2015-01-04
Lubuntu doesn't give a desktop notification when a device is ejected, but in Xubuntu, when I use the Eject option, the desktop notification says "..the device has been safely removed from the system". I infer from this that Eject provides for safe removal. I only see the option "Safely Remove" on Ubuntu and Ubuntu Mate.

---

### Post by Dennis N on 2015-01-05
If you try:
```
sudo udisksctl power-off --block-device /dev/sdb
```
a test tells me you need to use the unmount option before power-off:
```
sudo udisksctl unmount --block-device /dev/sdb
```
The sequence of these two in this order -- unmount and power off -- can be a small script and it does work, but would you want this option in all right click file manager menus? I don't think so. That is what would normally happen if you implement with Lubuntu's custom actions. Further, would either of these commands check for open files and warn you? Not tested. That would have to be part of it.

---

