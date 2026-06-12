---
title: "How to handle blocks in partitions that cannot be recovered"
date: 2014-07-10
forum: New to Ubuntu
---

### Post by Krithivasan on 2014-07-10
Hi

I am absolutely new to Linux.

My desktop has two partitions.  In the first partition Redhat Linux is installed and the second was not used.

I encountered problem of badblocks and redhat linux was not booting.  I installed Ubuntu in the second partition and was able to successfully login to ubunto

I run testdisk which identified some blocks in the partitions that cannot be recovered.  Relevant part of the logfile is as follows:

     Linux                59674   1  1 60310 254 57   10233336 [/]
     ext3 blocksize=4096 Large file Sparse superblock Backup superblock, 5239 MB / 4996 MiB
Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
Check the harddisk size: HD jumpers settings, BIOS detection...
The harddisk (500 GB / 465 GiB) seems too small! (< 749 GB / 698 GiB)
The following partitions can't be recovered:
     Linux                30305  44 12 91106  59 25  976769024
     ext4 blocksize=4096 Large file Sparse superblock Recover, 500 GB / 465 GiB
     Linux                30310 232  3 91111 247 16  976769024
     ext4 blocksize=4096 Large file Sparse superblock Recover, 500 GB / 465 GiB
     Linux                30313   1  1 91114  16 14  976769024
     ext4 blocksize=4096 Large file Sparse superblock Recover, 500 GB / 465 GiB
     Linux                30313  19 43 91114  34 56  976769024
     ext4 blocksize=4096 Large file Sparse superblock Recover, 500 GB / 465 GiB
     Linux                30313  52 12 91114  67 25  976769024
     ext4 blocksize=4096 Large file Sparse superblock Recover, 500 GB / 465 GiB
     Linux                30318  77 32 91119  92 45  976769024
     ext4 blocksize=4096 Large file Sparse superblock Recover, 500 GB / 465 GiB

I need detailed steps to  make the badblocks as a partitiion and hide the partition so that I will be able to recover and use redhat linux.

Regards
Krithivasan

---

### Post by slooksterpsv on 2014-07-10
I'm not sure how you'd exactly do that, but if you download a burn a Hiren's boot cd, we can use a utility that may be able to fix those bad blocks - doesn't always work, but it did for me with my other computer. The HDD sectors were failing and it read and wrote the data it read over and over again on the bad sectors and fixed them. Not saying it'll help but it's worth a shot. The app I used on the CD was DRevitalize, there's another one which people have claimed work for them and that's HDAT2. It's just worth a shot.

Someone may have some other useful information that may help, but that's the advice I can offer.

---

### Post by Krithivasan on 2014-07-11
Hi

Is there any other option available?

Regards

Krithivasan

---

