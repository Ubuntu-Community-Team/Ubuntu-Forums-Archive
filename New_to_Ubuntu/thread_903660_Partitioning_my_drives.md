---
title: "Partitioning my drives"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by nougat03 on 2008-08-28
I'm not sure which option to choose when I get to the partition screen in the install.

I'd like to combine two drives, but I'm not sure how to do it. 


Sorry for being such a noob, I know there's already a ton of partition threads.

---

### Post by halitech on 2008-08-28
are you doing the install from the Live CD or an alternate cd?

---

### Post by nougat03 on 2008-08-28
> **halitech said:**
> are you doing the install from the Live CD or an alternate cd?

Alternate. I downloaded Ubuntu and burned it to a disc, then rebooted.

---

### Post by halitech on 2008-08-28
is there anything on the drives you want to keep?

---

### Post by nougat03 on 2008-08-28
> **halitech said:**
> is there anything on the drives you want to keep?

No, I already moved everything onto my external.

---

### Post by halitech on 2008-08-28
ok, you can't actually combine 2 drives but you should have an option to do a manual partitioning, select 1 drive for / (root) and swap and the other for /home. are the drives close to the same size or are they different sizes?

---

### Post by nougat03 on 2008-08-28
> **halitech said:**
> ok, you can't actually combine 2 drives but you should have an option to do a manual partitioning, select 1 drive for / (root) and swap and the other for /home. are the drives close to the same size or are they different sizes?

Different sizes. One is 200GB and the other is 60GB. How do I select a drive for root, swap, and home?

on the manual screen I have:
/dev/sda
/dev/sda1  ntfs
free space
/dev/sdb
/dev/sdb1  fat32

---

### Post by sandysandy on 2008-08-28
ur  / partition will have to be formatted to ext3 and SWAP as SWAP.

i see u have NTFS and FAT 32 partition. u can get rid of it if not using it in future. or are u planning on dual booting with windows.

see these links on installing ubuntu

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

[https://help.ubuntu.com/8.04/installation-guide/i386/index.html](https://help.ubuntu.com/8.04/installation-guide/i386/index.html)

regards

---

### Post by anmolgautam on 2008-08-28
hey please help me out!!!!
actually i ve a hard disk of 160gb.....while partitioning i made a partition of 10gb for est3 and 4 gb for swap....the rest i left as free space....i thought maybe i cud use it as storing space....but it is not visible....wat to do so dat i can restore it back.....

---

### Post by sandysandy on 2008-08-28
for partitioning have a look at gparted which is part of Ubuntu live CD or available at

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

(burn it as iso image to make bootable CD.

then pop in CD drive and reboot computer.)

see tutorial

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

regards

---

### Post by nougat03 on 2008-08-28
> **sandysandy said:**
> ur  / partition will have to be formatted to ext3 and SWAP as SWAP.

i see u have NTFS and FAT 32 partition. u can get rid of it if not using it in future. or are u planning on dual booting with windows.

see these links on installing ubuntu

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

[https://help.ubuntu.com/8.04/installation-guide/i386/index.html](https://help.ubuntu.com/8.04/installation-guide/i386/index.html)

regards

I've read that I should resize a partition but I don't think I'm able to.
-https://help.ubuntu.com/community/forum/installation/Partitioning
-https://help.ubuntu.com/community/WindowsDualBoot

When I'm at the partition screen in the install, I only have three options: Guided - use entire disk, Guided - use the largest continuous free space, and Manual. After I select manual, and select a drive like sda1 I can only edit the partitions type, choose to format the partition, and give it a mount point.

Maybe that's my problem.. they don't seem to be mounted. I was thinking they would mount after I partitioned the disks and finished installing.

---

### Post by ajgreeny on 2008-08-28
> **anmolgautam said:**
> hey please help me out!!!!
actually i ve a hard disk of 160gb.....while partitioning i made a partition of 10gb for est3 and 4 gb for swap....the rest i left as free space....i thought maybe i cud use it as storing space....but it is not visible....wat to do so dat i can restore it back.....
A bit of a hijack of the thread, which you really shouldn't do, but anyway, to answer your question, you need to format the free space as /home and then edit your fstab file to make sure it is used and mounted at boot time.  If you have not yet used Ubuntu much and have not got a lot of files of your own on it, it's probably easier to start again and make sure you set the free space as an ext3 partition and format and mount it as /home at the manual partitioning stage.

---

### Post by ajgreeny on 2008-08-28
> **nougat03 said:**
> I've read that I should resize a partition but I don't think I'm able to.
-https://help.ubuntu.com/community/forum/installation/Partitioning
-https://help.ubuntu.com/community/WindowsDualBoot

When I'm at the partition screen in the install, I only have three options: Guided - use entire disk, Guided - use the largest continuous free space, and Manual. After I select manual, and select a drive like sda1 I can only edit the partitions type, choose to format the partition, and give it a mount point.

Maybe that's my problem.. they don't seem to be mounted. I was thinking they would mount after I partitioned the disks and finished installing.

When you get to the partitioning point, choose Manual, choose the disk to use, then make the partitions of the size and file type you want (ext3 for / and /home, and swap for the swap partition).  You need to manually set the mount points in the installation partitioning and when you click OK, the partition table will be rescanned after each partition is made, and there will be a small button with a tick in it for all those partitions to be formatted.  Just go with it and at the end when you actually do the install, they will all be formatted and mount points set for the installation.

---

### Post by anmolgautam on 2008-08-28
hey dat thing is not on my live cd...and not able to access wifi

---

