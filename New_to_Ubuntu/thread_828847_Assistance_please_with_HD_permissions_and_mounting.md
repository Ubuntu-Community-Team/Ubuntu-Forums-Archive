---
title: "Assistance please with HD permissions and mounting"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by njigsaw on 2008-06-14
I have two HDisks one smaller 40GB with my OS on it and a second 120GB one for all my storage.

Through my "places" link I can see the 120GB HD but I cannot write to it, rename it or do anything with it due to "unable to determine permissions".

Could someone help walk me through setting the permissions so that I can get this 120GB HD accessible for read write please. I note also that it doesnt appear to be mounted at all from the fstab. Is this correct?
It was formatted from a problem giving ntfs to ext3.

Attached are copies of the fstab output and also fdisk.

Many thanks in advance.

Neal

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4689e496-32b8-447d-855d-17560d275c8d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=e982ab18-18fd-4996-bafc-2b85db96d17d none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


neal@neal-desktop:~$ sudo fdisk -l

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00b900b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4905    39399381   83  Linux
/dev/sda2            4906        4998      747022+   5  Extended
/dev/sda5            4906        4998      746991   82  Linux swap / Solaris

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcfca8540

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14946   120053713+  83  Linux

---

### Post by dracayr on 2008-06-14
Is /dev/sda2 the 120GB HD? In that case, you are correct: It doesn't seem to be present in your /etc/fstab. are you sure that's all of the output?

> It was formatted from a problem giving ntfs to ext3.

To what was it formatted?? what do you mean "giving ntfs to ext3"?

does ```
sudo mount /dev/sda2
``` work?

dracayr

---

