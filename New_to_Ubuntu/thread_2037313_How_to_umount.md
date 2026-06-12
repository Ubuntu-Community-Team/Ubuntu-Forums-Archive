---
title: "How to umount?"
date: 2012-08-04
forum: New to Ubuntu
---

### Post by Houmie on 2012-08-04
Hi,

I do a ```
sudo fdisk -l
```

And can see my USB drive:

```
Disk /dev/sdb: 2063 MB, 2063597568 bytes
64 heads, 62 sectors/track, 1015 cylinders, total 4030464 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62     4027519     2013729    c  W95 FAT32 (LBA)

```

Now I try to unmount it:
```
umount -f /dev/sdb1
```

But the disk is still there. Nothing happens.

What am I missing?
Thanks

---

### Post by HermanAB on 2012-08-04
It won't unmount if it is in use and fdisk is not the way to check whether the device is mounted.  Try the mount command:
$ sudo mount

---

### Post by ryanyeah on 2012-08-04
You need to unmount it from the location it is mounted to, rather than the device itself.

ie. umount /mnt

If the filesystem is busy and you want to force it to umount:

umount -l /mnt

---

