---
title: "Reset device numbering after removing device? /dev/sda, sdb, sdc, etc"
date: 2015-01-19
forum: New to Ubuntu
---

### Post by spockswhitepants on 2015-01-19
I had a hardware RAID array on /dev/sdb (looks like a single disk to linux). I added another drive and transfered the data off (sdc). Now I removed the array and I am left with sda and sdc with sdb being the non-existant array. Is there a way to free up sdb and force sdc to move to sdb?

---

### Post by Jonor on 2015-01-23
Try temporarily removing the other drive, booting, then adding it again.

---

### Post by nerdtron on 2015-01-25
> **spockswhitepants said:**
> I had a hardware RAID array on /dev/sdb (looks like a single disk to linux). I added another drive and transfered the data off (sdc). Now I removed the array and I am left with sda and sdc with sdb being the non-existant array. Is there a way to free up sdb and force sdc to move to sdb?

sda, sdb, or sdc means they are on the sata port 1, port 2, and port 3, You can move the new hard drive to the same port as the /dev/sdb.

---

### Post by bab1 on 2015-01-25
> **nerdtron said:**
> sda, sdb, or sdc means they are on the sata port 1, port 2, and port 3, You can move the new hard drive to the same port as the /dev/sdb.
This is not nessesaraly true.  The device name is assigned by the kernel as it is enumerated (found).  If you where to add a usb flash, ssd or hard drive the device name can change.

The OP could assign the names (sda, sdb, etc.) using udev rules ( see [here]("http://stackoverflow.com/questions/18422500/how-do-you-swap-dev-sda-with-dev-sdb"), but there really is no reason to do that.  The partitions (sda1, sdb2, etc.)  should referred to by their UUID (blkid) or assigned a lablel.  The device name assigned by the kernal is only relevent to the kernel, which manages that information internally.

---

