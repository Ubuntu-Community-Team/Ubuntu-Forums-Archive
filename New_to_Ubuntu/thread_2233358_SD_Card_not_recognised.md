---
title: "SD Card not recognised"
date: 2014-07-08
forum: New to Ubuntu
---

### Post by r3bol on 2014-07-08
My SD Card seems to be having some problems. It doesn't automount, and gParted doesn't recognise it. Trying sudo fdisk -l, I get 
```
Disk /dev/mapper/cryptswap1: 2135 MB, 2135949312 bytes
255 heads, 63 sectors/track, 259 cylinders, total 4171776 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf6ddc267

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

```
...where it should contain info about /dev/sdc
How can I get my card back? Thanks.

---

### Post by r3bol on 2014-07-08
Actually the output above might not even be related to the card as it is 4GB.

---

### Post by r3bol on 2014-07-08
I managed to get it to a windows pc and format it there. It now recognises it in ubuntu again.

---

