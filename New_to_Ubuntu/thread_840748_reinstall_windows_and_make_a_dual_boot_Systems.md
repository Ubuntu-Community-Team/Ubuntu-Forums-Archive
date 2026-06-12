---
title: "reinstall windows and make a dual boot Systems"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by AnasZ on 2008-06-25
I am new in Linux and have installed ubuntu to my computer and deleted all partitions, i want now to reinstall windows and make a dual booting OSs.
my hard now has the following partitions: 
1)/dev/sda1   ntfs         13.68
2)unallocated              14.01
3)/dev/sda3   ext3         25.61 
4)/dev/sda2   extended      2.59
5)/dev/sda6   Linux-swap    1.15
6)/dev/sda5   fat32         1.44

please advice how can I reinstall windows, i have tried to boot from the recovery cd but after formating nothing happening?:confused:

---

### Post by Titan8990 on 2008-06-25
Do you not have an actual Windows installation disk?


You should note that it quite a bit harder to install Windows second in a dual boot environment but possible.

---

### Post by macness on 2008-06-26
AnasZ: What have you tried?

Also you'll need [this guide]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0") later for sure!

---

### Post by AnasZ on 2008-06-26
well I used the recovery CD of my laptop but after it is formating the 1st partition of the disk it starts again the ubuntu and no windows is showing in the starting menu while booting??

---

### Post by macness on 2008-06-26
> **AnasZ said:**
> well I used the recovery CD of my laptop but after it is formating the 1st partition of the disk it starts again the ubuntu and no windows is showing in the starting menu while booting??

You mean in the GRUB menu? as in the list of operating systems you can boot to?

if so follow [this guide]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0")and use the super GRUB disk to recover your windows boot.

---

### Post by melrom on 2008-06-26
Is he wanting to recover though?

If you deleted all your partitions, windows won't be there anymore. but if ubuntu is still there, then you did not, in fact, delete all of your partitions.

Do you want to recover a Windows install or do a whole new one?

---

### Post by DGortze380 on 2008-06-26
At this point, with the fact that you only have a recovery CD and not a windows install CD your best bet is probably to do the following:

1) Back up ALL data, it will be long gone by the time we're done.

2) Run the Ubuntu Live CD

3) In a terminal type sudo gparted

4) Delete all partitions

5) Create one new NTFS partition using the whole drive (if it will let you, I dont know if gparted supports ntfs), if not you will have to use a partitioner that supports ntfs, your recovery disk may or may not have one.

6) Boot your recovery disk

7) Attempt to install to you ntfs partition

8a) If this works, install windows, boot your ubuntu live cd, double click install and partition your free space as desired.

8b) If your recovery cd can not partition the drive you will need to use the ubuntu live cd (or knoppix live dvd) to fix your mbr. Post here is that happens and I'll try to find the reference for doing so.

EDIT: You can try this if you have a problem with your mbr afterwards. No guarantees as I haven't done it myself. [http://www.knoppix.net/forum/viewtopic.php?t=27696](http://www.knoppix.net/forum/viewtopic.php?t=27696)

---

### Post by fidamehran on 2008-06-26
> **DGortze380 said:**
> At this point, with the fact that you only have a recovery CD and not a windows install CD your best bet is probably to do the following:

1) Back up ALL data, it will be long gone by the time we're done.

2) Run the Ubuntu Live CD

3) In a terminal type sudo gparted

4) Delete all partitions

5) Create one new NTFS partition using the whole drive (if it will let you, I dont know if gparted supports ntfs), if not just shutdown after deleting your partitions.

6) Boot your recovery disk

7) Attempt to partition and install using the whole drive

8a) If this works, install windows, boot your ubuntu live cd, double click install and partition your free space as desired.

8b) If your recovery cd can not partition the drive you will need to use the ubuntu live cd (or knoppix live dvd) to fix your mbr. Post here is that happens and I'll try to find the reference for doing so.

EDIT: You can try this if you have a problem with your mbr afterwards. No guarantees as I haven't done it myself. [http://www.knoppix.net/forum/viewtopic.php?t=27696](http://www.knoppix.net/forum/viewtopic.php?t=27696)
I think this is the best option. Installing Ubuntu after Windows is easier than installing Windows after Ubuntu.
If you are a complete newbie like me, you can also use the new "Wubi" run process of installing Ubuntu inside Windows (available only from version 8.04 onward). That would relieve you from the drive partitioning hassle that most of us newbies face. Moreover, using the "Wubi" will make no new partition, rather install in a virtual partition inside the existing Windows partition.
I'm not an expert yet. But just felt like saying something. Sorry if I said something wrong.

---

### Post by macness on 2008-06-26
> **fidamehran said:**
> I think this is the best option. Installing Ubuntu after Windows is easier than installing Windows after Ubuntu.
If you are a complete newbie like me, you can also use the new "Wubi" run process of installing Ubuntu inside Windows (available only from version 8.04 onward). That would relieve you from the drive partitioning hassle that most of us newbies face. Moreover, using the "Wubi" will make no new partition, rather install in a virtual partition inside the existing Windows partition.
I'm not an expert yet. But just felt like saying something. Sorry if I said something wrong.

You didn't say anything wrong ;)

The facts are that it is most definitely easier to install Ubuntu after windows, but I think his concern is losing his current data on the windows drive... if that's not a problem - start from scratch! (windows first of course :))

---

### Post by DGortze380 on 2008-06-26
> **macness said:**
> You didn't say anything wrong ;)

The facts are that it is most definitely easier to install Ubuntu after windows, but I think his concern is losing his current data on the windows drive... if that's not a problem - start from scratch! (windows first of course :))

See, I didn't think he had a current windows install, just single boot ubuntu... problem is he has a restore disk (as in cd/dvd), not a windows install disk.

---

### Post by netwurkpunk on 2008-06-26
I was just about to post a new thread on a similar topic, my questions have been answered except one:  If i completely wipe my current XP installation with my recovery cd and start fresh, how much is the minimum space i can give to the XP partition and still have it be useful ( note all i want to do in XP is occasionally sync/charge my ipod touch)?

---

### Post by macness on 2008-06-26
> **netwurkpunk said:**
> I was just about to post a new thread on a similar topic, my questions have been answered except one:  If i completely wipe my current XP installation with my recovery cd and start fresh, how much is the minimum space i can give to the XP partition and still have it be useful ( note all i want to do in XP is occasionally sync/charge my ipod touch)?

Well theoretically you only need iTunes installed then and you're music library can still be on your ubuntu partition (i do this too with my ipod) but you'll need drivers in windows to read your linux partition which you can get [here]("http://www.fs-driver.org/"). 

I'd recommend 7-10 GB for windows then (and that's a bit excessive for XP) but JUST in case you wanted to install something else.

---

### Post by DGortze380 on 2008-06-26
> **netwurkpunk said:**
> I was just about to post a new thread on a similar topic, my questions have been answered except one:  If i completely wipe my current XP installation with my recovery cd and start fresh, how much is the minimum space i can give to the XP partition and still have it be useful ( note all i want to do in XP is occasionally sync/charge my ipod touch)?

gtkpod has linux drivers for iPods, you can buy music on Amazon.com that doesn't have any DRM?? restrictions.

---

### Post by macness on 2008-06-26
> **DGortze380 said:**
> gtkpod has linux drivers for iPods, you can buy music on Amazon.com that doesn't have any DRM?? restrictions.

I don't want to get into a iPod tangent (probably left best to another thread) but does gtkpod work with touch? i thought not... but then again I dont have a touch (I use rythmbox to sync music with my ipod mini).

---

### Post by DGortze380 on 2008-06-26
> **macness said:**
> I don't want to get into a iPod tangent (probably left best to another thread) but does gtkpod work with touch? i thought not... but then again I dont have a touch (I use rythmbox to sync music with my ipod mini).

no idea. sorry. definitely ask in another thread though.

---

### Post by netwurkpunk on 2008-06-26
> **macness said:**
> Well theoretically you only need iTunes installed then and you're music library can still be on your ubuntu partition (i do this too with my ipod) but you'll need drivers in windows to read your linux partition which you can get [here]("http://www.fs-driver.org/"). 

I'd recommend 7-10 GB for windows then (and that's a bit excessive for XP) but JUST in case you wanted to install something else.

Thanks

---

### Post by AnasZ on 2008-06-28
Hi Dan, I've booted from Ubuntu CD and now i had one ntfs partition, so i've rebooted from Windows recovery CD but it did not give me any option and reformated the HD then asked me to restart after taking out the CD and the same error message.
now i have nothing in HD even ubuntu is not booting from the HD; only from live CD. what should i do, thanks

---

### Post by DGortze380 on 2008-06-28
> **DGortze380 said:**
> At this point, with the fact that you only have a recovery CD and not a windows install CD your best bet is probably to do the following:

1) Back up ALL data, it will be long gone by the time we're done.

2) Run the Ubuntu Live CD

3) In a terminal type sudo gparted

4) Delete all partitions

5) Create one new NTFS partition using the whole drive (if it will let you, I dont know if gparted supports ntfs), if not you will have to use a partitioner that supports ntfs, your recovery disk may or may not have one.

6) Boot your recovery disk

7) Attempt to install to you ntfs partition

8a) If this works, install windows, boot your ubuntu live cd, double click install and partition your free space as desired.

8b) If your recovery cd can not partition the drive you will need to use the ubuntu live cd (or knoppix live dvd) to fix your mbr. Post here is that happens and I'll try to find the reference for doing so.

EDIT: You can try this if you have a problem with your mbr afterwards. No guarantees as I haven't done it myself. [http://www.knoppix.net/forum/viewtopic.php?t=27696](http://www.knoppix.net/forum/viewtopic.php?t=27696)

Follow the link at the bottom of this post, you probably have to fix your mbr.
could you please be more specific about what you did? after booting your recovery cd, did it go through the whole install? or give you an error first? did you see "grub loading" when you restarted the comp without the recovery cd? Nothing will boot off the hard drive right now, you've deleted anything that was on it. You need to get the recovery disk to reinstall before windows will boot off the hard drive.

---

