---
title: "External hard drive mounted read-only"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by Mardok45 on 2008-11-17
**Ignore this topic, it turned out to be a problem with the hard drive, not Ubuntu.**
I need to backup my data onto an external hard drive.  The hard drive is being mounted as read-only.  When I try to change the permissions to be able to write to the hard drive, it gives me an error message saying that the mount is read only.

I'm using Hardy.  How can I get around this?

EDIT:  Not sure if this matters, but the hard drive is NTFS.

---

### Post by drs305 on 2008-11-17
I added some after you edited to include that it is an ntfs drive. Read the entire entry before accomplishing the first part of this entry.

Please post the results of:
```

sudo blkid
mount
cat /etc/fstab

```

When we get that information we can either give you recommendations on how to alter your fstab file or change permissions/ownership of the mount point.

Also, if you have several external partitions or drives, please tell us which one you are having the problems with.


Added after your EDIT - **Read this first**:
You can install ntfs-config to get write capabilities on this NTFS drive. See this post I made earlier today:
[http://ubuntuforums.org/showthread.php?t=984861#5]("http://ubuntuforums.org/showthread.php?t=984861#5")

---

### Post by Mardok45 on 2008-11-17
I have to type all this out on a seperate machine since the one with the images doesn't have internet acces.  I omited anything that doesn't have anything to do with the problem.
> 
OUTPUT OF BLKID:
/dev/sda1: UUID="d80f36d7-6a7c-4a66-8692-de5f438480e3" TYPE="ext3"
/dev/sda5: TYPE="swap" UUID="7e71ab7e-db03-43bc-a7a1-0e5a414ad0a2"
/dev/sdb10: TYPE="hfsplus"

OUTPUT OF MOUNT:
/dev/sdb10 on /media/BOOT type hfsplus (rw, nosuid, nodev,uhelper=hal)

FSTAB:
UUID=7e7lab7e-db03-43bc-a7al-0e5a414ad0a2 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0


This is the only external device.

---

### Post by drs305 on 2008-11-17
Are you sure you copied the info for the correct partition? The output you provided indicates it is formatted as 'hfsplus' and not ntfs. Also, it is listed as sdb10, indicating there are a lot of partitions on that device. I haven't used that type of format but believe it is for Apples.

If this is in fact the one you want access to, this entry in fstab should give you rw access to it:

```

/dev/sdb10 /media/BOOT hfsplus rw,exec,auto,users 0 0

```

If you find another device with ntfs formatting, the entry would be (if your uid is 1000):
```

/dev/sdb10 /media/*yourmountpoint* ntfs-3g defaults,umask=027,uid=1000 0 0 

```

---

