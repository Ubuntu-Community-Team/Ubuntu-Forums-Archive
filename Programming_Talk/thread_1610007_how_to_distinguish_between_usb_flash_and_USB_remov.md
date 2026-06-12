---
title: "how to distinguish between usb flash and USB removable hard disk"
date: 2010-10-31
forum: Programming Talk
---

### Post by onlythegod on 2010-10-31
I plan to write a program that can distinguish between USB flash drivers and removable driver.I believe linux can tell apart them because gnome displays the usb flash and USB removable hard disk in different icons.
but, I have no idea about how to implement it.
Can anyone help me or give me some ideas?

---

### Post by Barrucadu on 2010-10-31
I'm not sure about this as I don't have a flash drive to test with, but perhaps /sys/block/sdX/uevent. For example, here's for my USB HDD:

```
 >>>  cat /sys/block/sdc/uevent
MAJOR=8
MINOR=32
DEVNAME=sdc
DEVTYPE=disk
```

---

### Post by onlythegod on 2010-10-31
> **Barrucadu said:**
> I'm not sure about this as I don't have a flash drive to test with, but perhaps /sys/block/sdX/uevent. For example, here's for my USB HDD:

```
 >>>  cat /sys/block/sdc/uevent
MAJOR=8
MINOR=32
DEVNAME=sdc
DEVTYPE=disk
```
the method doesn't work.the usb flash shows devtype=disk

---

### Post by onlythegod on 2010-10-31
> **Barrucadu said:**
> I'm not sure about this as I don't have a flash drive to test with, but perhaps /sys/block/sdX/uevent. For example, here's for my USB HDD:

```
 >>>  cat /sys/block/sdc/uevent
MAJOR=8
MINOR=32
DEVNAME=sdc
DEVTYPE=disk
```
the method doesn't work.the usb flash shows devtype=disk

---

