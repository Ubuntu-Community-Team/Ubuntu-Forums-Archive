---
title: "[SOLVED] Can't Mount Corrupted Flash Drive Partition"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by blendmaster on 2008-09-21
Hello!

So I was messing around with my flash drive partitions, and I've managed to make most of the drive unusable (an interesting trick, but unfortunately not what I was going for).

I use *mount /dev/sdf* (to mount the entire drive) and I get:

```
mount: can't find /dev/sdf in /etc/fstab or /etc/mtab

```

I use *mount /dev/sdf1* (to mount the first FAT32 partition that's already mounted) and I get:

```
mount: according to mtab, /dev/sdf1 is already mounted on /media/disk
mount failed
```

I use *mount /dev/sdf2* (to mount the second, corrupted partition) and I get:

```
mount: can't find /dev/sdf2 in /etc/fstab or /etc/mtab

```

*fdisk -l* produces:

```
Disk /dev/sdf: 2006 MB, 2006974464 bytes
255 heads, 63 sectors/track, 244 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1          95      763056    b  W95 FAT32
```

My drive was originally 2GB, but it is now about 770MB. Any help (if this is fixable) would be appreciated.

---

### Post by blendmaster on 2008-09-21
Oh well. When in doubt, use GParted.

I deleted both partitions... so if anyone ever has this problem and wants a corrupted drive back, remember the basic tools of Linux (in this case, GParted).

---

