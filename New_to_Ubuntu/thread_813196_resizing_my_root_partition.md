---
title: "resizing my root partition"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by jaydoc on 2008-05-30
[IMG]http://i31.tinypic.com/2dkihy0.png[/IMG]

That's how my partitions look.....

I had another Linux OS in the 10 GB space that's unallocated.

Virtualbox is not letting me install XP.... its crashing halfway through the installation process all the time.... No error message generated... I don't know where to look for it either...

I suspect its because i'm not able to create sufficient diskspace for it as my root partition is very small.

I have only 512 MB RAM, that might be the reason too... However, my problem now is, how can I allot the empty space to my /root partition....?

I want to do it without having to reinstall...! Can I...?

Help.

---

### Post by Duck2006 on 2008-05-30
You can but it's going to take a lot of work and time to do it. Your have to add it to the extended partition, then take it of the other of the extended and then add it to the next partition and remove the space from the other partition, ect ect.

---

### Post by Oldsoldier2003 on 2008-05-30
Partition juglling takes a lot of time.Usually I just back up everything and delete the partitions and create new ones, then restore.

---

### Post by ladr0n on 2008-05-30
If you don't want to deal with the tangled mess of moving all of those partitions around, you could create VBox's virtual drive image on another partition.  Delete the virtual machine you are currently trying to install windows on, and create a new one.  When it prompts you for the drive image, put it on one of your other partitions (just make sure it's something you can mount anytime you need to use virtualbox).  You'll probably still want to get around to shuffling that extra space onto your / partition at some point, but that will at least allow you to get VBox working now.
--Edit--
Oldsoldier's idea is better, if you have a good way of backing up your data.

---

### Post by jaydoc on 2008-05-30
Hey...

Thanx to all....

It WAS the disk space that was the PROBLEM.

I just used the unallocated 10 GB space and the install went without a hitch. I never knew one could install a virtualbox drive on a folder other than the default root partition...!

But, how do I make Virtual XP "see" and "work" with the FAT32 storage drives on my PC...?

At the moment it doesn't do that....!

---

### Post by housam on 2008-05-30
Are the Fat32 drives mounted and seen through ubuntu ?

---

### Post by aks2008 on 2008-06-05
Hi
 Go to your filesystem in ubuntu. Under media see if your fat32 partitions are visible.(they will be named as 56 GB media or similar) If they are, then mount them by clicking on them.
 Install guest additions in your virtualbox XP. Add fat32 partitions in virtualbox shared folders. Do map network drive in virtualbox XP. Your fat32 partitions should be visible in your XP my computer usually as "z" drive.
 I used to need to mount those partitions after every reboot by clicking on them before starting my virtualbox machine.

---

