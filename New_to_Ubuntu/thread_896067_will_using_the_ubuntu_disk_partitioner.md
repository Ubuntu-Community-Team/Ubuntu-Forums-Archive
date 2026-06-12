---
title: "will using the ubuntu disk partitioner"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by medioxcore on 2008-08-20
completely wipe my windows partition?

i read somewhere that it would, but i can't find that article now.

i want to dual boot, but am hesitant because i don't have a windows cd.  only a restore partition.

suggestions?

thank you!

---

### Post by jerome1232 on 2008-08-20
It will if you tell it to.

During the install there's several options. (I don't remember the exact words) one of them is to resize the partition and install to free space, that's the one you would want.

---

### Post by ApUUbunU on 2008-08-20
I do not have any previous experience partitioning a drive with the Ubuntu tool, but I can say that that partitioning a drive needs some form of backup at the very least. 

If the partition is made correctly, then your windows partition will be fine, the free space will be used to make the Ubuntu partition.

Occasionally, partitoning can go wrong, and mess up your hard drive, causing you to lose valuable data. I would recommend backing up your hard drive which you intended to partition on to DVDs, or onto another hard drive.

Also, have you thought about using Wubi installation of Ubuntu, it allows a dual-boot, with out any repartitioning.

[http://wubi-installer.org/](http://wubi-installer.org/)

Apu

---

### Post by medioxcore on 2008-08-20
yeah, I have all my stuff backed up, I'm just worried that if my windows partition is wiped, I won't be able to get it back because I don't have my windows cd.

and I have never heard of wubi. how does that work?

---

### Post by lavinog on 2008-08-20
Usually computers with a recovery partition have a program in windows that lets you burn the recovery partition to cd/dvd...you may want to try that...keep in mind you only get one shot at that (due to licensing restrictions) once you loose that cd you have no choice but to use the recovery partition.

On one of my computers the burn to cd feature failed so I used partimage to backup the recovery partition to dvd...you can look into that if the above is not available.

as for setting up a dual boot:
Make sure you have a decent amount of free space on your windows partition. To prep the install you want to shrink the windows partition down to allow for at least 10-15 gigs free (of course the more the better, but windows is more hd thirsty than ubuntu).
You can shrink the partition with gparted (on the live cd.) The installer probably has an option to do it for you, but I haven't used it.
In gparted: select the main NTFS partition and select shrink/grow then move the slider to make room. Keep in mind also that your new size for the windows partition must be 10% free other wise file system errors can occur in windows.
click on apply...the resize process will most likely take some time...(hours depending on how many files on your windows partition)

after that you should be good to go with the install.
Another note...some recovery partitions will erase the grub bootloader when you boot to them...try to avoid booting to it if you can...if you do and it does mess up grub, you can repair grub with the live cd.

---

### Post by ApUUbunU on 2008-08-20
I think you should really listen-in if you havent heard of Wubi. If you look on the link I sent you, you will find out that its a windows installer for Ubuntu. It works by creating a virtual drive, which is mounted on startup of Ubuntu, but cannot be seen in Windows.

The great thing about Wubi, is that it doesn't need any repartitioning at all. The install is easy, and if you don't like Ubuntu, you can uninstall it really quickly from Windows. However, performance is (slightly) lower than a normal installation, and you do not have the option to hibernate. I use Wubi my self, and would reccomend giving it a try before partitioning your drive. 

I am planning to partition a drive to ext3 myself so I can properly install Ubuntu (Im really beggining to like it). Up till now, Wubi has been great.

---

### Post by sandysandy on 2008-08-20
how many partitions do u have. 

if u need to resize ur XP partition to make room for creating ubuntu partitions, do [COLOR="Red"]***defragment***[/COLOR] XP before resizing.

take backup!

read carefully these links on dual boot

[http://apcmag.com/how_to_dual_boot_w...lled_first.htm](http://apcmag.com/how_to_dual_boot_w...lled_first.htm)

[http://www.howtoforge.com/dual_boot_..._ubuntu_feisty](http://www.howtoforge.com/dual_boot_..._ubuntu_feisty)

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)


as u can see from the links there are various options for installing ubuntu, in some options it does not touch another partition and  only uses selected partition ( in case more than one partition exist). 

see this excellent gparted tutorial in case u need to make partitions manually before installing ubuntu

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)


regards

---

### Post by pi.boy.travis on 2008-08-20
> **ApUUbunU said:**
> I do not have any previous experience partitioning a drive with the Ubuntu tool, but I can say that that partitioning a drive needs some form of backup at the very least. 

If the partition is made correctly, then your windows partition will be fine, the free space will be used to make the Ubuntu partition.

Occasionally, partitoning can go wrong, and mess up your hard drive, causing you to lose valuable data. I would recommend backing up your hard drive which you intended to partition on to DVDs, or onto another hard drive.

Also, have you thought about using Wubi installation of Ubuntu, it allows a dual-boot, with out any repartitioning.

[http://wubi-installer.org/](http://wubi-installer.org/)

Apu

> **medioxcore said:**
> yeah, I have all my stuff backed up, I'm just worried that if my windows partition is wiped, I won't be able to get it back because I don't have my windows cd.

and I have never heard of wubi. how does that work?

> **ApUUbunU said:**
> I think you should really listen-in if you havent heard of Wubi. If you look on the link I sent you, you will find out that its a windows installer for Ubuntu. It works by creating a virtual drive, which is mounted on startup of Ubuntu, but cannot be seen in Windows.

The great thing about Wubi, is that it doesn't need any repartitioning at all. The install is easy, and if you don't like Ubuntu, you can uninstall it really quickly from Windows. However, performance is (slightly) lower than a normal installation, and you do not have the option to hibernate. I use Wubi my self, and would reccomend giving it a try before partitioning your drive. 

I am planning to partition a drive to ext3 myself so I can properly install Ubuntu (Im really beggining to like it). Up till now, Wubi has been great.

Wubi is good for trying out Ubuntu, but I have had lots of problems with it.  I have tested it on three computers, Vista, and XP, and I found the system a bit unstable.  Disk performance is also impacted.  If you are serious about switching to Linux, I recommend a full installation with a dedicated partition.  I have had several machines running like this for quite some time, and they are functioning wonderfully.  You may want to request a Windows CD from your manufacturer.  I have requested them from Dell several times.  It is a good Idea to have one on hand, just in case.   The importance of backups can't be stressed enough.  No partitioning tool is perfect! 

Hope this helps!!

---

### Post by jerome1232 on 2008-08-20
Agreed, I didn't stress the backups when I should have, make it a habit to make regular backups. :) One day you will be glad you did.

---

