---
title: "Mounting an external usb hard drive automatically on startup"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by peterjakey on 2008-08-09
Hi, I would like to know how to automatically mount an external HDD on startup because I have my music on there and Amarok wont see it untill i mount it myself

---

### Post by BennyHill on 2008-08-09
This might be helpful for you

[http://ubuntuforums.org/showthread.php?t=802699]("http://ubuntuforums.org/showthread.php?t=802699")

---

### Post by cdtech on 2008-08-09
Is this a USB drive?

It doesn't mount when you plug it in?

With it plugged in do a "sudo fdisk -l" and lets see which drive it is.

---

### Post by peterjakey on 2008-08-09
Its USB

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xace22e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15935   127997856    7  HPFS/NTFS
/dev/sda2           15936       19457    28290465    5  Extended
/dev/sda5           15936       19306    27077526   83  Linux
/dev/sda6           19307       19457     1212876   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

---

### Post by cdtech on 2008-08-09
It does auto mount through USB. If you look under "Places" you'll see the drive is there. If you do a reboot with it plugged in it will still be there.

You should not use "/etc/fstab" to auto mount a USB device, it will only create error's.

Just point Amarok to that drive under "Places".

**P.S.**
HAL (Hardware Abstraction Layer) is used to detect a USB device when it is plugged in.

---

