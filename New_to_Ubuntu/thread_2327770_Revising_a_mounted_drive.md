---
title: "Revising a mounted drive"
date: 2016-06-14
forum: New to Ubuntu
---

### Post by albertramsbottom on 2016-06-14
Hi

I have a linux VM in Azure running Ubuntu 14:04

I have build a Moodle application using a mounted additional disk /dev/sdc1

This disk is small to start but I am trying to figure out how I can increase the size on the ext4 file system on this disk.  I have stopped (delocated), the disk in Azure, made it 2GB larger and restarted the VM.

My mount is at /var/www/html and is

```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        29G  2.9G   25G  11% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            835M  8.0K  835M   1% /dev
tmpfs           168M  408K  168M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            840M     0  840M   0% /run/shm
none            100M     0  100M   0% /run/user
none             64K     0   64K   0% /etc/network/interfaces.dynamic.d
/dev/sdc1       2.9G  519M  2.3G  19% /var/www/html
/dev/sdb1        69G   52M   66G   1% /mnt
```

My sdc1 drive is 2.9 GB (original size), but is actually now been expanded to 5GB in Azure

How do I expand the file system without dataloss??

Many Many Thanks for ant help

---

