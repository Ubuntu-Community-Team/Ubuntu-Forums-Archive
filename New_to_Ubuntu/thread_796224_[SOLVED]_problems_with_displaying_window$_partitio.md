---
title: "[SOLVED] problems with displaying window$ partition in 8.04"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by sharks on 2008-05-16
i installed ubuntu 8.04 and when i logged on i did not find any windows partition on the desktop.i had to go to System-->computer and then double click all the partitions on the side pane to get it displayed on the desktop.but whenever i restart my system i cant see those partitions.

---

### Post by kpkeerthi on 2008-05-16
Those partitions will not get auto-mounted by default. To have them auto-mounted at system startup you need to edit /etc/fstab. 

Can you post the output of ```
sudo fdisk -l
```?

---

### Post by kpkeerthi on 2008-05-16
If the partitions are NTFS formated, check this out
[http://ubuntuforums.org/showpost.php?p=4757851&postcount=6](http://ubuntuforums.org/showpost.php?p=4757851&postcount=6)

---

### Post by hermes0710 on 2008-05-16
Can you post your /etc/fstab file?
In which /dev/sd?? entry is your windows partion mounted?
**If you don't know post the output of this command:
```
sudo fdisk -l
```**


What is its filesystem (ntfs/fat)?

---

### Post by sharks on 2008-05-16
The output is > Disk /dev/sda: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaf92af92

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1364    10956298+   7  HPFS/NTFS
/dev/sda3            1365        9730    67199895    f  W95 Ext'd (LBA)
/dev/sda5            1365        2716    10859908+   7  HPFS/NTFS
/dev/sda6            3953        5864    15358108+   7  HPFS/NTFS
/dev/sda7            5866        7777    15358108+   7  HPFS/NTFS
/dev/sda8            7778        9730    15687441    7  HPFS/NTFS
/dev/sda9            3920        3952      265041   82  Linux swap / Solaris
/dev/sda10           2717        3919     9663066   83  Linux

Partition table entries are not in disk order


---

### Post by kpkeerthi on 2008-05-16
Those are NTFS formatted. Follow the link I posted earlier.

---

