---
title: "Installing Ubuntu on an Acer  laptop"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by a.v.l on 2008-06-20
My new Acer 7720 laptop seems to have two 250GB hard drives. Drive 1 has two partitions "C" with around 98GB and "D" with around 111GB. On C"" I think is Vista and on "D" I think is the 7 GB recovery partition. "E" is empty with around 230 GB.

When I try and install Ubuntu and select manual install I have several choices to choose from and I'm unsure which one is the E drive. can someone advise please?

I'd also like to know how can I use the remainder of the space on the drive with the recovery partition.

---

### Post by Duck2006 on 2008-06-20
Use the partition tool from within vista to partition some space for your linux install, Then install ubuntu.

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by avtolle on 2008-06-20
Presuming you are using the Live CD, back out of the partitioner, get to the console (Alt+Ctl+F1), and there do```
sudo fdisk -l
``` and post the output, please.

---

### Post by a.v.l on 2008-06-20
> **avtolle said:**
> Presuming you are using the Live CD, back out of the partitioner, get to the console (Alt+Ctl+F1), and there do```
sudo fdisk -l
``` and post the output, please.

This is the result.

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeb4de1f0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1402    11261533+  27  Unknown
/dev/sda2   *        1403       15918   116592640    6  FAT16
/dev/sda3           15918       30402   116342784    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeb4de1f1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS
ubuntu@ubuntu:~$

---

