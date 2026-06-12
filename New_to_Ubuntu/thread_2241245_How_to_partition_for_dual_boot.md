---
title: "How to partition for dual boot?"
date: 2014-08-25
forum: New to Ubuntu
---

### Post by rems2 on 2014-08-25
Hey guys,

need help regarding  on how to partition for a dual boot. 

Currently i'm running windows 7 with 3 partitions. 
C: (windows) Primary 80gb
D: Primary  60 gb (Empty and was created for ubuntu)
E: Primary  160 gb (for my data)

The "D drive" is also primary and was created initially for ubuntu. 
But after seeing some forums on how to dual boot i'm confused as some say that we need to create a "Logical drive" for ubuntu.

What is the optimum partitioning scheme for dual booting ubuntu with windows 7?  

Thanks in advance.

---

### Post by slickymaster on 2014-08-25
Hi rems2, welcome to the forums.

I'd advise you to have a read at [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Jahidul_Hamid on 2014-08-25
Creating logical partitions is a good practice because primary partitions have a limitation of not going further than 4 partitions. If your data partition is empty then you should delete the D and E partition to create two or three new logical partitions. If you intend to create Two partitions then it should be like this:
ext4 with mount point /  (60 gb logical partition)
ntfs with no mount point (160 gb logical partition as data partition)

---

### Post by Elfy on 2014-08-25
> **rems2 said:**
> Hey guys,

need help regarding  on how to partition for a dual boot. 

Currently i'm running windows 7 with 3 partitions. 
C: (windows) Primary 80gb
D: Primary  60 gb (Empty and was created for ubuntu)
E: Primary  160 gb (for my data)

The "D drive" is also primary and was created initially for ubuntu. 
But after seeing some forums on how to dual boot i'm confused as some say that we need to create a "Logical drive" for ubuntu.

What is the optimum partitioning scheme for dual booting ubuntu with windows 7?  

Thanks in advance.

Given that you've created a partition in windows at D - if you created it in windows it'll be pretty much useless.

Remove it via windows so you've got 60Gb unallocated.

Boot the ubuntu disk and then create partitions there. You can create an extended in the 60Gb space then be free to do the logicals inside that. 

Just be careful in the live session - _it will not call anything C: or D: or E: _

---

### Post by Topsiho on 2014-08-25
I am not sure that you should repartition the Windows7 computer in Linux (with GParted). I learned (the hard way) that you should [COLOR="#FF0000"]prepare space for Linux[/COLOR] in Windows it self, then restart Windows to make sure that Windows recognized the new situation on the hard disk. With enough unallocated space for Ubuntu, which can be partitioned using GParted). Please let readers correct me if I'm wrong.

There is nothing mysterious with primary, extended and logical partitions.
Windows should be installed first, in the first primary partition on the first hard disk: /sda1
Only 4 primary partitions are possible, per hard disk.
One of the primary partitions on a disk can be sacrificed for an extended partition, in which a large number of logical partitions can be accomodated.

Usually the root partition of Ubuntu is installed in a primary partition (eg. /sda3, using ext4), but may also in a logical partition (e.g. /sda5), and /home and swap partions in logical partitions (eg. /sda6  (ext4) and /sda7 (swap)).

When you create a logical partitition, and there is not yet an extended partition, an extended partition is created automatically, and in this the new logical partition. The extended partition would be in this example /sda2. If an extended partition exists, the logical partition is placed in it. It should have enough room for this, but you created enough unallocated space for Ubuntu already in Windows as a first step ...

Hope this helps :)

Topsiho

---

### Post by Ksiencha on 2014-08-25
I used [**this guide**]("https://www.liberiangeek.net/2012/04/dual-boot-windows-7-and-ubuntu-12-04-precise-pangolin/") when I was creating my dual-boot with Windows 7 and Ubuntu 14.04

You can see my partition scheme  in the attached image

I really hope it'll help you somehow because I'm totally not an advanced user.

---

### Post by stalkingwolf on 2014-08-25
This is what mine looks like
sda1 swap
sda2 mint 13
sda3 mint17
sda 4 storage.

Yours will be something like

SDA1  windows.  Then I would go this way
sda2     swap
sda3   ubuntu
sda4 storage
however if you think you might want another partition later  you will want to make sda4 an extended /logical and put your storage in side that.

---

### Post by oldfred on 2014-08-25
Please post this from live installer.

sudo fdisk -lu
sudo parted -l

If you create more than 4 partitions in Windows it converts to dynamic partitions not an extended and logical partitions. And dynamic is Windows proprietary and does not work with Linux. It is somewhat like LVM in being logical partitions overlaying the physical 4 primary partitions.
In fdisk it will show as SFS meaning you have dynamic partitions. Windows has no undo or convert back to basic partitions, but some third party tools may work.

---

### Post by rems2 on 2014-08-27
Hey guys,

sorry for the late reply. was out of town.

Thanks a lot for the awesome replies , through which i managed to install ubuntu with the dual boot. 
And i learned some good things as well through your replies.

Again thanks a lot.:p

---

### Post by Ksiencha on 2014-08-27
It's always nice to see when the thread is Solved. thx to you too :)

---

