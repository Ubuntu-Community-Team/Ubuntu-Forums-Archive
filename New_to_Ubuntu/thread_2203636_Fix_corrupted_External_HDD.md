---
title: "Fix corrupted External HDD"
date: 2014-02-04
forum: New to Ubuntu
---

### Post by cupid.callin on 2014-02-04
I was messing around with my Seagate External USB Drive when I messed it up. I tried emptying it up using

```
sudo dd if=/dev/zero of=/dev/sdb
```

but after that gparted shows it only to be ~2GB and it doesn't let me create partition.

The drive does work as I was able to write data to it (and also copy from it to my PC) after formatting it using GParted. But it stopped working just a moment after it.

fdisk:

```

Disk /dev/sdb: 2051 MB, 2051555328 bytes
4 heads, 32 sectors/track, 31304 cylinders, total 4006944 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007fad6


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048     4005887     2001920    b  W95 FAT32



```

I think its gone for good this time but I would still like to give it a last try. There is no data on the External HDD.

---

### Post by sudodus on 2014-02-04
What drive is it? Maybe someone will recognize it and can give relevant advice, if you specify the ***model and size*** of the drive.

Shutdown and cold boot your computer, and try with ***gparted*** again!

Start with Device -- Create partition table

and see if it still only recognizes 2 GB.

Also, please post the output of this command

```
sudo parted -l
``` and let us check how much of that information that is correct.

---

