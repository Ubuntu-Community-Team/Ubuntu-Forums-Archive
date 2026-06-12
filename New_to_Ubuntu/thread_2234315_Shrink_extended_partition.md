---
title: "Shrink extended partition"
date: 2014-07-14
forum: New to Ubuntu
---

### Post by kevin100 on 2014-07-14
I have my laptop set to dual boot with windows 7. I have a ~250gb hard drive. 

My windows 7 partition(NTFS), /dev/sda1 is 145.38GiB, with 71.77GiB used, and 73.61GiB free.

My Linux partition(extended), /dev/sda3 is 75.68GiB. Inside my Linux partition, I have /dev/sda5 (ext4) which is 10.74GiB, 8.03 used, and 2.71 unused. And /dev/sda6 (Linux swap) which is 3.11GiB. Also inside my extended partition, is 61.83GiB unallocated space. 

I want to move that 61.83GiB of unallocated space, out of my extended Linux partition (/dev/sda3) and use it for my windows 7 partition(/dev/sda1).

I am using gparted off of a live disk so no partitions are locked. I cannot shrink /dev/sda3 at all. And I can't make /dev/sda1 larger. I can't drag and drop anything, and I'm not sure what to do.

---

### Post by ibjsb4 on 2014-07-14
Try turning swap off (right click on your swap partition).

If that does not work, please post a pic of your partition layout in gparted.

---

### Post by Impavidus on 2014-07-14
Maybe your swap partition is mounted? When you start a live session and it finds a swap partition on the hard disk, the live session will mount it automatically. In gparted, right click in swap, select swap off. Then you can resize the extended partition. Right click, resize or edit or whatever it's called, and tell it what you want. Don't use gparted to expand the Windows partition (even though most of the time it seems to work). Use gparted to put  the unallocated space next to the Windows partition and then use Windows  tools to expand the Windows partition. And make sure you've got backups of all important stuff, but you should always have those, even when you're not changing partitions.

Note that you can only move the boundaries of the extended partition into unallocated space, not occupied by sda1, sda5 or sda6. /dev/sda5 and sda6 won't move automatically when you resize sda3, so you may have to move them first.

Also note that 11GB is small for a Linux partition. It may be wise not to move all 63GB to Windows. It's unlikely that you'll notice the difference between a 195 and a 206 GB Windows partition (only 5%), whereas an 11 or 22GB Linux partition makes a huge 100% difference. But that is up to you.

---

### Post by oldfred on 2014-07-14
Another alternative is to just create a NTFS partition using the unallocated space. The new d: drive should then appear in Windows and can be mounted in Linux for shared data.

Otherwise if unallocated is at end of extended partition you have to move a lot of partitions. Moving has a higher risk, so make sure all data is well backed up. You have to have the unallocated at the beginning of the extended partition so you can shrink it from the left to in effect move unallocated out of the extended partition.

---

### Post by at_first_light on 2014-07-15
> I have my laptop set to dual boot with windows 7. I have a ~250gb hard drive. 

My windows 7 partition(NTFS), /dev/sda1 is 145.38GiB, with 71.77GiB used, and 73.61GiB free.

My Linux partition(extended), /dev/sda3 is 75.68GiB. Inside my Linux  partition, I have /dev/sda5 (ext4) which is 10.74GiB, 8.03 used, and  2.71 unused. And /dev/sda6 (Linux swap) which is 3.11GiB. Also inside my  extended partition, is 61.83GiB unallocated space. 

I want to move that 61.83GiB of unallocated space, out of my extended  Linux partition (/dev/sda3) and use it for my windows 7  partition(/dev/sda1).


Based on sizes in the information given it sounds like your disk looks something like this:

[ATTACH=CONFIG]254749[/ATTACH]

My understanding is that you want to take the free space from the extended partition, add it to the free space after Windows 7, and add all that free space to the Windows 7 partition? This should be achievable, but I'm not sure if Ubuntu will boot afterwards as some operating systems don't do well with moves. I've never moved Ubuntu before so perhaps someone can confirm? I would expect that it won't though.

> **at_first_light said:**
> [SIZE=4][COLOR=#ff0000]_**WARNING:**_[/COLOR][/SIZE]
Before  engaging in any kind of partitioning be aware that if a failure occurs  you could loose access to all the data on the partitions involved, and  in a worst case scenario all data on the entire drive. It is good form  to back up your entire drive before doing any form of partitioning on  it. This means backing up your files, and operating systems in manner  that is restorable.

Related Threads:
[http://ubuntuforums.org/showthread.php?t=2234758](http://ubuntuforums.org/showthread.php?t=2234758)



I have been able to duplicate your problem in Gparted. After performing the steps below the partition doesn't allow me to move it to the right or left.

1. Boot up a livecd, Open Gparted, click on your swap partition, and choose "swap off".
2. Right click on your extended partition, and choose "resize/move".

I would suggest a work around might be after choosing "resize/move" just shrink the partition. Then use some kind of disk cloning software like DD to make an image of the extended partition. Delete the partition, expand the Windows partition as desired, create a new blank partition and restore the image you made of the extended partition to it. I'm not sure if you can image an extended partition? You might have to image the 2 logical partitions as 2 separate images, and then restore them individually. As mentioned before I don't know if Ubuntu will be able to boot if you move it!

---

