---
title: "External HDD is 'read only'"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by 449 on 2008-05-21
It happened randomly, and I'm not able to put any files on my external harddrive. How can I fix this?

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b00fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2898    23278153+   7  HPFS/NTFS
/dev/sda3            2899       38848   288768375   83  Linux
/dev/sda4           38849       38913      522112+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2         637     5108670    5  Extended
/dev/sdb2             638       30401   239079330    b  W95 FAT32
/dev/sdb5               2         637     5108638+   6  FAT16

```

---

### Post by TeoBigusGeekus on 2008-05-21
If your drive is sdb and it's mount point is /media/disk, try
```
sudo chown -R yourusername /media/disk
```

---

### Post by 449 on 2008-05-21
> **TeoBigusGeekus said:**
> If your drive is sdb and it's mount point is /media/disk, try
```
sudo chown -R yourusername /media/disk
```

Didn't work. :(

---

### Post by 449 on 2008-05-24
Anyone?

---

### Post by tramir on 2008-05-24
I had a similar problem some time ago and managed to solve it this way. Can you post the exact command you ran?

---

### Post by 449 on 2008-05-24
> **tramir said:**
> I had a similar problem some time ago and managed to solve it this way. Can you post the exact command you ran?

[http://img211.imageshack.us/img211/4103/screenshotgv2.png](http://img211.imageshack.us/img211/4103/screenshotgv2.png)

---

### Post by chrisccoulson on 2008-05-24
chown or chmod will not work with FAT partitions as they have no concept of Unix file permissions. And if a volume is 'read-only', no amount of chmod-ing or chown-ing will fix it, regardless of what filesystem is.

First of all, you need to understand why the volume is being mounted read-only. It could be due to specifying 'ro' as a mount option, or due to filesystem errors (the most likely)

Please have a look at one of the following threads
[http://ubuntuforums.org/showthread.php?p=5033077]("http://ubuntuforums.org/showthread.php?p=5033077")
[http://ubuntuforums.org/showthread.php?t=770498]("http://ubuntuforums.org/showthread.php?t=770498")
[http://ubuntuforums.org/showthread.php?p=4942422]("http://ubuntuforums.org/showthread.php?p=4942422")

They should solve your problem:)

---

### Post by sayakb on 2008-05-24
Did you try mounting it from CLI?
```
sudo mkdir /media/disk1
sudo mount -t /dev/sdb1 /media/disk1
```

Plus, can you provide me the link to the theme you're using :)

---

### Post by 449 on 2008-05-24
[http://img211.imageshack.us/img211/4103/screenshotgv2.png](http://img211.imageshack.us/img211/4103/screenshotgv2.png)[IMG]http://img211.imageshack.us/img211/4103/screenshotgv2.png[/IMG]

I tried all of the options that it listed ,but it still will not format. (I forgot how I went from fat32 to nothing.) :confused:

---

