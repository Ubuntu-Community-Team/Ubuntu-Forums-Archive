---
title: "Ubuntu 8.04 HDD Mount Problem"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by Dark Star on 2008-05-14
Well after install I don't have any problem but after the update my partitions aren't getting mounted automatically.. Also after I click them they get Mounted but as a Disk Not as Hard Drive

Any Idea about the problem !:mad:

---

### Post by TeoBigusGeekus on 2008-05-14
You need to edit your fstab file.
```
gksudo gedit /etc/fstab
```

---

### Post by hermes0710 on 2008-05-14
Can you post the /etc/fstab file?

---

### Post by Dark Star on 2008-05-14
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=23c1deaf-4020-46da-8803-03bee09a3e07 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=8bd4d2de-165a-46d0-a3da-85e9db62a11c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

I guess Mount [updated through Manager] only caused the problem and removed entries from /etc/fstab

---

### Post by hermes0710 on 2008-05-14
What is device you want to mount? (I mean which /dev/ entry do you want to mount?)

---

### Post by Dark Star on 2008-05-14
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0dd6c6bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3187    25599546    7  HPFS/NTFS
/dev/sda2            3188        8287    40965750    f  W95 Ext'd (LBA)
/dev/sda3            8288        9607    10602900   83  Linux
/dev/sda4            9608        9729      979965   82  Linux swap / Solaris
/dev/sda5            4406        5737    10699290    7  HPFS/NTFS
/dev/sda6            5738        8287    20482843+   7  HPFS/NTFS
/dev/sda7            3188        4405     9783522    7  HPFS/NTFS

Partition table entries are not in disk order

```

My NTFS partitions \:)

---

### Post by hermes0710 on 2008-05-14
Follow this "How To"

[http://ubuntuforums.org/showthread.php?t=142481]("http://ubuntuforums.org/showthread.php?t=142481")

---

