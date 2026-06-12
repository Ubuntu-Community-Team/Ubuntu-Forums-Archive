---
title: "Can i resize my FILESYSTEM partition?"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by diwas on 2008-08-14
Yes, is there anyway to do it??

Also...can i "move" my entire FILESYSTEM partition's data to another partition and still make the OS work???

---

### Post by nicedude on 2008-08-14
Yes you can resize your filesystem partition easily with gparted partition editor which is either installed already or in the repositories, I think though that parted may be installed by default ( which would also do it ) but I like Gparted better ( very similar to each other super close to the same thing ). Anyway if gparted isn't installed here is the command to install it,

sudo apt-get install gparted

just paste that in a terminal to install it, then go to top bar tab called System -then-> Administration -then-> partition editor and you will be in gparted. All you do then is select the partition you want to resize and select to resize it. This will take awile though since it moves allot of  data around on the disk to do your biding :-)

*** EDIT
OOPS I didn't see you meant your Ubuntu partition you are booting to , answer is still yes but you just must do it with a live CD wither Ubuntu or they make a Gparted live boot CD as well that you can download and burn for FREE and makes a great tool for working on Linux and Windows PC's filesystems. Reason for this is you can't edit a mounted partition and you can't unmount the main system partition if it is booted up, same would apply for windows and other OS's.

As to moving all data on a partition to a different disk, I am sure you can do it but it might require some work more advanced than using gparted to resize will. It really would depend though on whether you were going to remove the old disk and just plug in a new one, if thats the case then as long as you moved the EXT3 main & SWAP partitions from drive A to drive B in the same positions they took on drive A ( partitions have the same location on the disk as in sda1 goes to first partition to become new sda1 and same for swap partition ). In that scenario you would still have to run a live CD ( either Ubuntu disk or live GRUB disk ) to reinstall grub to your new hard disks MBR ( master boot record ) so its kinda advanced I guess but I am sure that people here have threads on reinstalling grub and would help you.


Hope this helps you figure out your situation, but I would start with the disk resize since that is both easy and should be trouble free :-)

---

### Post by technotitclan on 2008-08-14
you can resize the partition by booting to you ubuntu live cd. your looking for "partition editor" which i believe is located in system/admin if not its located some were in the main menu and does have the name "partition editor" it uses a slider bar lay out to change partition sizes

---

### Post by cdtech on 2008-08-14
That's correct you have to use the live CD to manipulate the "root" partition. You can use the "dd" command to copy data to another partition as well, to see a complete howto on the "dd" command see my sig.......

Hope this helps.....

---

### Post by diwas on 2008-08-14
Oh thank u guys. 

Actually this is my scenario. I have an old Hard Drive which is PATA (my board is pretty old) and few days before i bought a SATA hard drive and a converter(SATA to PATA) for my board. And now i have plenty of hard drive space. 
But i actually want to install ubuntu(and XP dual boot) in SATA Hard Drive. But im told that in order to boot frm another hard disk i have to change the jumper settings and all....(is it true??)


Oh by the way...resizing my partition using LIVE CD won't affect my current ubuntu will it?? I mean all the softwares installed...all the settings....everything will be there wont it??

---

### Post by cdtech on 2008-08-14
Resizing wont effect your data, as long as you don't interrupt the process.

Booting from a secondary hard drive can be accomplished using the BIOS settings, or you could change the hard drive order via cables, then you would need to change the jumpers.

---

### Post by diwas on 2008-08-14
Does that mean that i can change the boot device from BIOS...widout changing the jumper and cables??? 
It would be so easy.

---

### Post by Irony on 2008-08-14
You can actually copy your entire install to another partition or an external drive;

[http://ubuntuforums.org/showthread.php?t=416710](http://ubuntuforums.org/showthread.php?t=416710)

You can then copy it back to your newly resized partition.

---

### Post by diwas on 2008-08-14
I have a question:

I have XP and Ubuntu dual boot. Is it possible to have XP in 1 hard drive and ubuntu in another???

---

### Post by jose_ramirez on 2008-08-14
Hi,

Yes, I don't see why not.

Regards,

Jose

> **diwas said:**
> I have a question:

I have XP and Ubuntu dual boot. Is it possible to have XP in 1 hard drive and ubuntu in another???

---

### Post by diwas on 2008-08-14
I was told (again) that u have to setup 1 hard drive as master and another as slave and only the master hard drive can boot up...and all..

(my cousin is constantly shouting from the other room...abt this!! haha)So i wud like to confirm abt it. Thats it.

---

### Post by logos34 on 2008-08-14
> **diwas said:**
> I have a question:

I have XP and Ubuntu dual boot. Is it possible to have XP in 1 hard drive and ubuntu in another???

sure.  Copy your ubuntu / and /swap to the new Sata [using Gparted]("http://gparted.sourceforge.net/larry/move/move.htm") on the ubuntu live cd.
Install Grub to the MBR of the new disk (see link my signature) and boot from that.  Edit your windows entry in /boot/grub/menu.lst to[ look like this]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk").

---

### Post by diwas on 2008-08-14
Thanks...this is a detailed version of what i completely wanted.


Is there anyway to do the same with XP???

---

### Post by logos34 on 2008-08-14
> **diwas said:**
> 
Is there anyway to do the same with XP???

yes--if you notice the Gparted link I gave you actually uses NTFS partition as an example.  I've never copied a windows system partition to another disk with Gparted, so I can't say whether or not you will have problems booting it afterward.   I've only used Partimage (unsuccessfully), but that's neither here nor there because NTFS support in Partimage is still 'experimental' (so it's hardy surprising it was unsuccessful!).

---

### Post by diwas on 2008-08-14
But its worth trying! 

I will let u know abt the problem...if it comes.

---

