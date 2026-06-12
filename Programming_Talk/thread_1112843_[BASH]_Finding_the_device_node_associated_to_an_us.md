---
title: "[BASH] Finding the device node associated to an usb stick"
date: 2009-04-01
forum: Programming Talk
---

### Post by jordan83 on 2009-04-01
Hi guys,

I need some help in writing some bash code that determines which device node is associated to a usb stick.

I need this because I own a small home server and I want to backup few files and folders on an usb stick that is permanently plugged in.

The problem is that every 2 weeks the server reboots and the device node associated to the usb stick may change to a different device node.
For example, last week the usb stick was available at */dev/sdc*, now it is at */dev/sdb*.

Do you have any idea/suggestion on how I could solve this problem, provided that I know the *vendor id* and the *device id* of the usb stick?

Thanks! :)

---

### Post by Backharlow on 2009-04-01
instead of using the /dev/device_that_changes to check the identification, use the Unique Identifier. It is actually unique. Think it is generated from the device model/serial or some such but it is persistent and unique.
try:
```
ls -l /dev/disk/by-uuid/
```
or,
```
sudo blkid
```

---

### Post by jordan83 on 2009-04-01
Thank you!!

This is a wonderful solution, I was preparing myself to dig into the wonders of udev and /sys but it seems that this is not necessary! :D

Great!

---

### Post by Backharlow on 2009-04-01
No problem. This is fairly common knowledge. I think though, most people start using UUID id when they start putting permanent additions into the fstab file, to mount various devices in custom ways at boot.

---

### Post by mdurham on 2009-04-01
> **Backharlow said:**
> instead of using the /dev/device_that_changes to check the identification, use the Unique Identifier. It is actually unique. Think it is generated from the device model/serial or some such but it is persistent and unique.
try:
```
ls -l /dev/disk/by-uuid/
```
or,
```
sudo blkid
```

Hi Backharlow, I don't think it's unique, I have two Toshiba 1GB USB sticks and each shows the same UUID. I guess it would be possible though to identify by LABLE wouldn't it?
Cheers, Mike

---

