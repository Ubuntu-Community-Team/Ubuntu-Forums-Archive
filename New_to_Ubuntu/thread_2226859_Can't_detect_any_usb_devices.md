---
title: "Can't detect any usb devices"
date: 2014-05-29
forum: New to Ubuntu
---

### Post by paul-loibl on 2014-05-29
I was trying to connect an external harddrive and then my printer, both through a hama usb port and directly
I'm guessing my usb ports are closed or something I'm not quite sure, tried with the different auto mount programs but nothing changed.
when I lsusb before and after pluging in, nothing changes...
yeah I'm lost, how do I fix this?
this is the message I get when I sudo fdisk -l

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00007201

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   625141759   312320001    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5          501760   625141759   312320000   83  Linux

Disk /dev/mapper/sda5_crypt: 319.8 GB, 319813582848 bytes
255 heads, 63 sectors/track, 38881 cylinders, total 624635904 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/sda5_crypt doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-root: 316.9 GB, 316854501376 bytes
255 heads, 63 sectors/track, 38522 cylinders, total 618856448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-swap_1: 2940 MB, 2940207104 bytes
255 heads, 63 sectors/track, 357 cylinders, total 5742592 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table
```

---

### Post by slickymaster on 2014-05-29
Please [use code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168"). It make the post clean, compact and more appealing, thus getting more attention from readers.

---

### Post by paul-loibl on 2014-05-29
thanks for the heads up slicky,
I hope somebody who's smarter than me has a clue what the output in my terminal means.
I already tried a lot of the things said on this forum but nothing has worked so far.
For now I'm planning on installing my old windows 7 so I can use my usbs through there.
that's only a quick fix though

---

