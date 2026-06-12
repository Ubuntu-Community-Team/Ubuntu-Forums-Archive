---
title: "80GB external only showing as 32GB"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by vocalstud69 on 2008-05-14
Okay, I'm not exactly a new user, but I think I screwed up on this one.  I had an old desktop hdd, so I went and got an external enclosure for it.  Yay.  Plugged it in, got whatever docs I wanted off of it, and then powered up fdisk to get rid of the partitions. Did that, but for some reason, fdisk no longer shows the hdd as a 80 GB hdd; it shows only 33.8GB under /dev/sdd. I tried running testdisk, and it shows only 32*** cylinders.  I don't know why this isn't working.  Help!  Tried plugging it into my girlfriends Vista box, and it won't even mount, but I don't know if that's Vista or my hdd.  I stay away from Vista if I can help it.

---

### Post by billgoldberg on 2008-05-14
> **vocalstud69 said:**
> Okay, I'm not exactly a new user, but I think I screwed up on this one.  I had an old desktop hdd, so I went and got an external enclosure for it.  Yay.  Plugged it in, got whatever docs I wanted off of it, and then powered up fdisk to get rid of the partitions. Did that, but for some reason, fdisk no longer shows the hdd as a 80 GB hdd; it shows only 33.8GB under /dev/sdd. I tried running testdisk, and it shows only 32*** cylinders.  I don't know why this isn't working.  Help!  Tried plugging it into my girlfriends Vista box, and it won't even mount, but I don't know if that's Vista or my hdd.  I stay away from Vista if I can help it.

Try using gparted instead.

---

### Post by shinobitux on 2008-05-14
What file system did you use to format it? Windows Vista should only mount FAT or NTFS file systems.

Try running fdisk on /dev/sdd (or whatever your drive is) but without superuser privileges.

How many partitions does it show?
What size are they?

I've formatted several external drives ext2 or ext3 and usually it goes something like this:

1. Find path to drive in /dev make sure it's unmounted
2. fdisk /dev/sdd and delete all partitions
3. mkfs.ext3 (sometimes mke2fs with journaling option) on entire physical drive (ie /dev/sdd and not /dev/sdd1)
4. fdisk /dev/sdd and make one large linux partition (physical partition 1)
5. mkfs.ext3 (or mke2fs with journaling) on physical partition /dev/sdd1
6. Mount drive and check available size (ie: df -h)

Hope that helps.

Edit:

I forgot to mention that you'll need to use mkfs and fdisk with superuser privileges.

Also, make sure you select the right drive and not any internal drives.

---

### Post by vocalstud69 on 2008-05-26
I actually got it to work, just because I'm an idiot.  It was a hardware problem, because there were the little things on the back that set the hard drive space to only be usable at 32 gbs.  I'm just that stupid, but I got it to work, thank god.

---

