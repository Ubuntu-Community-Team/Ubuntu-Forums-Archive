---
title: "Mount partitions"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by rbhigday on 2008-04-27
I have several partitions that are not mounting how do I fix this in fstab?

my first stab was this

```


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=171acda0-b66a-4406-ab7d-b810ab6d3302 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=d258b447-a47c-442a-b650-60c5ccd86e24 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/sdb7 /mnt/files hfsplus auto,defaults 0 0

```

Here is my fdisk -l results

```


Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16708   134206978+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12748   102398278+  83  Linux
/dev/sdb2           12749       19457    53890042+   5  Extended
/dev/sdb5           12749       12875     1020096   82  Linux swap / Solaris
/dev/sdb6           12876       16699    30716248+  83  Linux
/dev/sdb7           16700       19457    22153603+   b  W95 FAT32

Disk /dev/sdc: 2053 MB, 2053963264 bytes
129 heads, 31 sectors/track, 1003 cylinders
Units = cylinders of 3999 * 512 = 2047488 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1004     2005808    e  W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(1009, 128, 31) logical=(1003, 20, 30)


```

Thanks in advance

Richard

---

### Post by Can+~ on 2008-04-28
Open a terminal, and expand the width of the terminal so you can see everything:

```
ls -l /dev/disk/by-uuid/
```

This will yield the UUID's of your hard disks

eg. My UUID of my windows partition (on a old IDE harddisk)
```
4C0CD6990CD67D80 -> ../../hda1
```

Before we proceed, create a folder on the desired mounting point (if it doesn't already exist).

Edit the fstab and copy a line that already works, and attach the proper partition you want to mount.

```
# /dev/hda1
UUID=4C0CD6990CD67D80 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
```

The first is the UUID, then the mount point, the filesystem, and the rest are flags that should be there (for instance, one of them make the default usergroup the plugdev, so everyone in plugdev can access it).

Notice that you can name the mounting point as you want, for instance, I got a hard disk that is mounted on [FONT="Courier New"]/media/common[/FONT]

There might be an easier method, but this one worked for me when gutsy didn't want to pick up my "common" partition.

*edit* Also, could you add tags to your post? (On the bottom) For future reference.

*edit2* Now that I think about it, make a copy of the fstab, just for security reasons:

```
cp /etc/fstab ~/fstab_backup
```

---

