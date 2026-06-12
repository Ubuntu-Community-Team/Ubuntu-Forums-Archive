---
title: "partitioning problem"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by Falc7 on 2008-07-21
Hi
Before, i had just XP on the desktop computer, then using the LiveCD i made a partition and installed ubuntu. Recently i deleted and reinstalled XP, but not before making XP's partition smaller. Now i would like to move the free space that was created when i made XP smaller, and give it to ubuntu.

My problem is that it seems the data is now on two different HD. I have no idea why and i can't understand it, but i am sure that before they were the same disk, i will post a gparted screenshot later today, but for now here is the partition magic screenshot 

[http://img91.imageshack.us/my.php?image=79604121ze2.png](http://img91.imageshack.us/my.php?image=79604121ze2.png)

Any help much appreciated.

---

### Post by RuleMaker on 2008-07-21
First thing firs, don't use partition magic, it can cause many problems with partitions and the GRUB.
Go to control panel select "Administrative tools" then "Computer management".
(I'm talking from my memory maybe it's a bit different).
Right click on the free space and make a new partition.

---

### Post by candtalan on 2008-07-21
A very good partition manager that I have used a lot is parted magic, it is available as a live CD
[http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads](http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads)

Or you could use a ubuntu live cd which has a similar partition editor included.

Some of the confusion you see might be from using a windows oriented tool (partition magic?) because windows tends to regard partitions as 'disks'.

It is easier with parted because you will see partitions simply as they are, with disks known as physical items. It sounds as if you only really have one single hard drive, in what started as a conventional windows machine? If this is true then your hd will be hda or sda or similar, but there would be only one disk.

---

### Post by oedha on 2008-07-21
or gparted livecd at [http://gparted.sourceforge.net](http://gparted.sourceforge.net)

---

### Post by Falc7 on 2008-07-21
Here is  pic of the 2 parts of the hard disk
[http://img380.imageshack.us/my.php?image=screenshotkf1.png](http://img380.imageshack.us/my.php?image=screenshotkf1.png)
[http://img137.imageshack.us/my.php?image=screenshot1kt9.png](http://img137.imageshack.us/my.php?image=screenshot1kt9.png)

They do seem to be on different disks, i am very confused, as they were not before. Using gparted, how would i merge them?

---

### Post by louieb on 2008-07-21
Yep the computer has two hard drives. To make them look like one drive there is something called LVM (Logical Volume Management). its in the repositories.  I tried it once with Fedora. Now I don't use Fedora or LVM.

Just my two cent - take the unallocated space, create a partition, format it with the ext3 file system. And use it to store data in.
Good Luck.

---

### Post by Falc7 on 2008-07-24
Ok thank, i will try with LVM, and if that dosen't work, i will follow your suggestion

---

### Post by Falc7 on 2008-08-05
I have installed LVM, but i can't see it any the appliations menu, or the system administration menu

The reason i as suspicious as to whether i have 2 HDDs is that when i first used the ubuntu live cd to make the partition, it was displayed as 1 HD. Then i partition it, and suddenly, at precisely the same place in the HDD where i chose to make the partition, it divides into two HDDs.

I am sorry i haven't explained the above paragraph very well.

---

