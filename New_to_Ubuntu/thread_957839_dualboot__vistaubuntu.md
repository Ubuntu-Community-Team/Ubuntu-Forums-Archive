---
title: "dualboot  vista/ubuntu"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by sspletttstoeszer on 2008-10-24
Hi All,
I'm new to linux And dualboot OS's.
I have a laptop with 2 sata hard drives and would like to know
the steps to set up dualboot. I have been looking all over for them but unable to find them. Can anyone help me with this.
My laptop is a Toshiba X205 with core 2 duo 1.66, 4gb ram,
2 160gb 7200rpm HDs and Nvidia Geforce 8700M GT.
OS is Vista Ultimate 64 bit and I have download Ubuntu 8.04.1
64 bit.

Thank you,
scott

---

### Post by WRDN on 2008-10-24
I have found [this]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm") to be a good guide for dual booting with Vista installed first.
If you want to install Ubuntu on a different HDD to Vista, then run the LiveCD, select Install and at the partitioning stage, click Manual. Then, select to use the second of two hard drives, and click "Edit Partition". Create 3 partitions: a root partition (ext3 filesystem) with the mount point /, a home partition (again, ext3) with the mount point /home, and finally, a swap partition.

---

### Post by drtre on 2008-10-24
Try partitioning your hard drives in the Linux installation process. Just keep in mind what's your windows drive is and partition the rest as u wish. this partitioning is specific to Linux and u cannot use your Linux drives under windows os. Just choose one of the partitioned drives and install the linux. that should be ok. u'll c a menu on your pc start up from which u can choose which os to boot.

---

