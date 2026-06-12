---
title: "fstab is not mounting ntfs at startup"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by Vicfred on 2008-05-14
My ntfs partitions are not mounting when I reboot and I can't mount it once I logged in, it says that the unprivileged users can't mount it. This is my output of sudo fdisk -l

```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4462    35840983+   7  HPFS/NTFS
/dev/sda2            4463       30515   209270722+   f  W95 Ext'd (LBA)
/dev/sda5            4463       28473   192868326    7  HPFS/NTFS
/dev/sda6           30425       30515      730926   82  Linux swap / Solaris
/dev/sda7           28474       29689     9767488+  83  Linux
/dev/sda8           29690       30424     5903856   83  Linux

```

And this is my fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=cde84d00-27c9-4ae4-975a-18d44e31e119 /               reiserfs notail,relatime 0       1
# /dev/sda8
UUID=f3d33f2c-f4d1-4f9f-9518-125538f0eb2f /home           reiserfs relatime        0       2
# /dev/sda6
UUID=62538e7b-cf0b-46d4-9aec-c0f396848fd2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda1   	/media/disk  ntfs    nls=utf8,auto,user,fmask=0111,dmask=0000   0   0
/dev/sda5   	/media/disk-1  ntfs    nls=utf8,auto,user,fmask=0111,dmask=0000   0   0
```

---

### Post by PinkFloyd102489 on 2008-05-14
Check the file /etc/group to see if your username is listed beside of the "fuse" group. If not, do this in a terminal:

```
useradd -G fuse USERNAME
```

---

### Post by Vicfred on 2008-05-14
> **PinkFloyd102489 said:**
> Check the file /etc/group to see if your username is listed beside of the "fuse" group. If not, do this in a terminal:

```
useradd -G fuse USERNAME
```

I guess it is
```
fuse:x:107:vicfred
```

---

### Post by zeronothing on 2008-05-14
my fstab looks a bit different than yours. I made sure I had the ntfs-3g module installed and this is what I have in my fstab in order to mount my ntfs partitions at startup:

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sdd1 /media/Music ntfs-3g defaults 0 0
/dev/sda1 /media/Videos ntfs-3g defaults 0 0
/dev/sdb1 /media/Programs ntfs-3g defaults 0 0
/dev/sdc1 /media/Movies ntfs-3g defaults 0 0

---

### Post by PinkFloyd102489 on 2008-05-14
Check if these programs are installed in Synaptic:

```

ntfs-3g
ntfsprogs
ntfs-config
libntfs-3g23
libntfs10

```

---

### Post by Vicfred on 2008-05-14
i just installed these

ntfsprogs
ntfs-config
libntfs10

---

### Post by PinkFloyd102489 on 2008-05-14
Try to mount it now.

---

