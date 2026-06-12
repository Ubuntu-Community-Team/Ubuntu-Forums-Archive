---
title: "formatting mp3"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by ains on 2008-05-19
I need to format my mp3 but not to sure how to go about it..
I read this post:

[http://ubuntuforums.org/showthread.php?t=783135&highlight=formatting+an+mp3+player](http://ubuntuforums.org/showthread.php?t=783135&highlight=formatting+an+mp3+player)

But I am hesitant that I shall do something wrong... here's my output:
```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14219   114214086   83  Linux
/dev/sda2           14220       14593     3004155    5  Extended
/dev/sda5           14220       14593     3004123+  82  Linux swap / Solaris
Note: sector size is 2048 (not 512)

Disk /dev/sdb: 1989 MB, 1989148672 bytes
64 heads, 56 sectors/track, 271 cylinders
Units = cylinders of 3584 * 2048 = 7340032 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         271     1942416    b  W95 FAT32
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 56) logical=(0, 1, 1)
```

---

### Post by ivze on 2008-05-19
That, which size is 1989 Mb, must be your player. Use gparted gui tool (installs from Synaptic) to format it.

---

### Post by Cypher on 2008-05-19
Use this command to format the drive.
```

sudo mkfs.vfat /dev/sdb1

```

---

