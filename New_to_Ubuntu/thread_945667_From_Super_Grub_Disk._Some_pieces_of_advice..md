---
title: "From Super Grub Disk. Some pieces of advice."
date: 2008-10-12
forum: New to Ubuntu
---

### Post by adrian15 on 2008-10-12
Hi,

This is adrian15 from the [Super Grub Disk](http://www.supergrubdisk.org) project.

I still see that some of you still advise to run the fdisk -lu command from a terminal command for helping on boot or installation problems.

Although this command it is useful in a lot of situations I encourage you to test the new [Show Hard Disks Partitions Layout](http://www.supergrubdisk.org/wiki/Support_Rules#Run_partition_layout_option) option from Super Grub Disk (Which it is found at Support menu).

With this option you will be able to see the partitions from the BIOS point of view (which hard disk is the actual first one and which one is the actual second one). 

Each one of the partition show their size in human number format. Even some Operating Systems are detected and given their names.

```

fdisklu
1 (hd0,0) fat 70 MB WINDOWS
1 (hd1,0) ext2fs 83 GB Ubuntu 8.04.1 \n \l

```


**I also encourage** you to advise people to use **Boot Linux directly** options which have been improved so that you can boot your Linux even if Grub is not correctly installed (not relying on menu.lst).

I am going to improve Boot Linux directly with a fstab parser soon or later too.

Finally, if you find that some boot error is very strange and you do not know how to fix, do not hesitate to encourage other people to ask their questions on the [Super Grub Disk Forum](http://www.supergrubdisk.org/forum/index.php). Although you should read first the [Boot Problems and their solutions on the wiki](http://www.supergrubdisk.org/wiki/Boot_Problems) ;).

adrian15

---

