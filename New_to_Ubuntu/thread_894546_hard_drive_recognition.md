---
title: "hard drive recognition"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by gatordoc on 2008-08-19
Hello all,

I have freshly re-installed ubuntu (hardy heron) and now plugged in my backup HD (which is a slave to the DVD ROM). The boot HD is a newer SATA cable 
I cannot for the life of me get the thing to mount where it used to be as a folder called backup and the fstab looks like

/dev/hdb1 /backup auto defaults 0 0

i have no idea but when i do fdisk -l the HD comes up as sdb1? (I think)

how do you tell the fstab how to mount the HD?

Thanks

---

### Post by dstew on 2008-08-19
If fdisk -l shows the partition as /dev/sdb1, then use that name in fstab instead of /dev/hdb1. You can try it out first with the mount command from the terminal:```
sudo mount -t ext3 /dev/sdb1 /backup
```I assume the file system in the partition is ext3. If that works, then changing fstab should also work. If it does not work, post the output of ```
sudo fdisk -l
```and any errors from the mount command.

---

### Post by fahadsadah on 2008-08-19
Ubuntu does not distinguish between hdX* and sdX* on my machine. Everything shows up as sd, even though I have IDE disks rather than SATA, and no SCSI, RAID, or SATA controllers

I believe this is due to a change in the kernel that some other distros didn't adopt?

Having worked with distros such as Slackware and Gentoo, I am used to this peculiarity.

---

### Post by gatordoc on 2008-08-19
Ok I did what was suggested and it still does not work properly.

I did this originally and it seemed to mount but when i go to
cd /backup

none of the files on that disk are actually shown in the terminal, but can be accessed by going to Places-->250.1MB Media

here is fdisk -l

> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x61af3f30

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c59a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29644   238115398+  83  Linux
/dev/sdb2           29645       30401     6080602+   5  Extended
/dev/sdb5           29645       30401     6080571   82  Linux swap / Solaris

Disk /dev/sdc: 2079 MB, 2079850496 bytes
16 heads, 32 sectors/track, 7934 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        7934     2031088    e  W95 FAT16 (LBA)


I have 2 250MB drives only

---

### Post by gatordoc on 2008-08-19
bump

---

### Post by dstew on 2008-08-19
Did you get any error messages when you did ```
sudo mount -t ext3 /dev/sdb1 /backup
```?

---

### Post by egalvan on 2008-08-19
> **fahadsadah said:**
> Ubuntu does not distinguish between hdX* and sdX* on my machine. Everything shows up as sd, even though I have IDE disks rather than SATA, and no SCSI, RAID, or SATA controllers

**I believe this is due to a change in the kernel that some other distros didn't adopt?**

Having worked with distros such as Slackware and Gentoo, I am used to this peculiarity.

This is due to updated drivers in Linux; nothing specific to Ubuntu.

All drives are sdX,
  hdX is gone.

:popcorn:

---

### Post by jerome1232 on 2008-08-19
That's odd sdb looks like it's your os, sda looks likt it's your drive, sdc looks like a thumb drive.
Try this to figure out what's mounted where.  Probably your drive is auto mounting at /media/disk or /media/disk-1
```
mount
```

---

