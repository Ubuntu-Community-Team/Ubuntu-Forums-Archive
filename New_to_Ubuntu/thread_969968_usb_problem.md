---
title: "usb problem"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by s0undb0mbing on 2008-11-03
when i plug in my flash drive  ubuntu wont recognize it

---

### Post by dustman on 2008-11-04
Could you be a bit more specific? I mean, there's no telling what may have gone wrong if you just say that your USB flash drive doesn't get recognized. Please paste the output of the commands:

```
lsusb -v
```
```
sudo fdisk -l
```
after you have connected the device.

Also you might take a look at [[COLOR="Blue"]this[/COLOR]]("https://help.ubuntu.com/community/Mount/USB") link.

Cheers!

Radu

---

### Post by kansasnoob on 2008-11-04
Simply installing pmount from the repos makes all of my external drives hot-pluggable:

```
sudo apt-get install pmount
```

If you have an external drive formatted in NTFS you'll probably want to install either ntfs-config or ntfsprogs.

---

