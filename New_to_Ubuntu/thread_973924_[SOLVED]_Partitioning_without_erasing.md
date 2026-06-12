---
title: "[SOLVED] Partitioning without erasing"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by Karilex on 2008-11-07
Hello I have been using ubuntu for a few months now and I was wondering if it was possible to partition my disk without deleting all my data and also I used to have a version of vista saved on a separate part of my disk still the same but partitioned but since i installed ubuntu i can't find it do you think it may be that when i installed ubuntu it formated the entire disc if this is not the case how do i get access to this part of my disk to dual boot vista and ubuntu i know that most of what i said is wrong I don't really understand much about all this since I'm quite a newb thanks for your help (on a totally different subject is there an ubuntu wiki? I just didn't want to clutter up the forum with a thread just for this)
oh and i already have gparted installed so if you could give me instructions for this it would be nice but if you want me to install something else that's ok :)

---

### Post by bumanie on 2008-11-07
go to terminal and post the output of > sudo fdisk -land > sudo blkid

---

### Post by Karilex on 2008-11-07
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4aa04a9f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14219   114214086   83  Linux
/dev/sda2           14220       14593     3004155    5  Extended
/dev/sda5           14220       14593     3004123+  82  Linux swap / Solaris


/dev/sda1: UUID="08507bf1-99a7-48af-840d-5fed633b5381" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="cdd7e585-7f76-4cbb-a18f-d37f2b21880f"

---

### Post by bumanie on 2008-11-07
You unfortunately have deleted everything to do with vista. As you have been using ubuntu for a few months, I don't think it would be worth trying to recover anything - too much has probably been overwritten by now.

---

### Post by Karilex on 2008-11-07
Oh too bad thanks anyways could you please tell me how to partition a part of my disk without deleting anything so i can 
create a partition to dual boot with windows

---

### Post by redbob on 2008-11-07
You could do a resize of you major partition so you should have unpartitioned space to install windows within it.

---

### Post by mapes12 on 2008-11-07
Use a Live CD to run Gparted, not the version on your system. This is because if your HDD is running your OS it may not give you a true picture of all your partitions. The Live CD will. Get the iso here: [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

You may also find this guide helpful in planning your partions: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by Karilex on 2008-11-07
thanks but i have upgraded to ubuntu 8.10 and i only have a 8.04 live cd is that okay:confused:

---

### Post by Karilex on 2008-11-07
> **redbob said:**
> You could do a resize of you major partition so you should have unpartitioned space to install windows within it.

I would but i don't know how to

---

### Post by mapes12 on 2008-11-07
> thanks but i have upgraded to ubuntu 8.10 and i only have a 8.04 live cd is that okay

The version of Ubuntu you are running does not matter. You need to burn yourself a GParted Live CD ( [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) )  then put it in your machine and boot from it. It will ask you some questions about your system then a very clear GUI will appear detailing your partions. You can then make your changes from there.

---

### Post by boof1988 on 2008-11-07
> **mapes12 said:**
> The version of Ubuntu you are running does not matter. You need to burn yourself a GParted Live CD ( [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) )  then put it in your machine and boot from it. It will ask you some questions about your system then a very clear GUI will appear detailing your partions. You can then make your changes from there.

My understanding (and I believe that I have done this) is that the partitions can be manipulated using GParted as part of the Ubuntu LiveCD...  Am I remembering correctly or not?

To OP,
Also... It is fine to use a Ubuntu 8.04 LiveCD on the machine you currently have 8.10 installed on.  You could even try it and see since you can run the OS from the CD.

---

### Post by mapes12 on 2008-11-07
> My understanding (and I believe that I have done this) is that the partitions can be manipulated using GParted as part of the Ubuntu LiveCD

I use the Alternate installation CD as the Ubuntu Live CD sometimes doesn't work on my systems. The Alternate CD does not have access to applications such as GParted (well, not from what I've seen). Therefore, I always keep a GParted Live CD in my little collection of useful tools. However, if the poster can access GParted from an Ubuntu Live CD then that will save some work.

---

### Post by louieb on 2008-11-07
Just a few things to look at 1st it is helpful to know the 3 types of partitions 
logical, extended and primary. [Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm")

and here some Parted documentation from the folks at Gparted. [GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")

and last linux.com has a couple of videos showing you how to use Gparted to set up a dual boot. [Linux.com :: Dual-booting Windows and Linux the easy way (Linux.com videos)]("http://www.linux.com/feature/114157") 

Not hard once you have done it. Good luck.

---

### Post by kansasnoob on 2008-11-07
Here's a nice simple guide to follow:

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

---

### Post by Karilex on 2008-11-07
thanks a lot guys :)

---

