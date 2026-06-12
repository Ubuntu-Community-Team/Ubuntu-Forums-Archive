---
title: "partition won't show up"
date: 2012-05-03
forum: New to Ubuntu
---

### Post by ayanstein on 2012-05-03
how can I fix partition on my netbook, I think it has a 160gb drive and the other partition does not appear, only the 50gb partition shows up.

please help

Here's the result when i did a 

sudo fdisk lu

"Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbf8b2b4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1       264638462   312580095    23970817    5  Extended
/dev/sda2   *        2048   161583103    80790528   83  Linux
/dev/sda3       161585152   264636487    51525668    7  HPFS/NTFS/exFAT
/dev/sda5       264638464   312580095    23970816   82  Linux swap / Solaris

Partition table entries are not in disk order"

---

### Post by oldfred on 2012-05-03
From Windows you will not see the Linux partitions. It also looks like you have a very large swap which is for use when RAM is full.

Generally swap only needs to be the same size as RAM in GiB if hibernating.
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by ayanstein on 2012-05-03
> **oldfred said:**
> From Windows you will not see the Linux partitions. It also looks like you have a very large swap which is for use when RAM is full.

Generally swap only needs to be the same size as RAM in GiB if hibernating.
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
I only have ubuntu installed, yeah swap is too large ,I'll fix that after I finish fixing the partition issues, what do you think is the problem?

Thanks for the speedy reply :)

---

### Post by NikTh on 2012-05-03
> **oldfred said:**
> From Windows you will not see the Linux partitions. It also looks like you have a very large swap which is for use when RAM is full.

Generally swap only needs to be the same size as RAM in GiB if hibernating.
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
+1 

Hi , 
You have an extremely big swap partition.. almost 24GB ... .This is a big loss of space !!

---

### Post by oldfred on 2012-05-03
From liveCD does gparted not show all the partitions. Post a screen shot.

---

