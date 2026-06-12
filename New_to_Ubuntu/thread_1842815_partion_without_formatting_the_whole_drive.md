---
title: "partion without formatting the whole drive"
date: 2011-09-12
forum: New to Ubuntu
---

### Post by murderd2death on 2011-09-12
i have a few partitions, but the 2 main are for windows 7 and ubuntu. ubuntu is taking up to much space, and i want to partition a piece of it back to ntfs without formatting the whole OS. how can i do that?

the ubuntu partition i have in particular doesnt have any important info yet so im not to worried about any damages, but any settingsand programs i can save would be nice. 

windows is 280G
ubuntu is 140G
i want to knock ubuntu down to around 50G and allocate the rest to ntfs. specifically to the original windows partition in C if possible.

regards

---

### Post by dave01945 on 2011-09-12
if you use a live cd/usb you can use gparted (**this is on the ubuntu live cd/usb**) to resize the ubuntu  partition (**as long as there is enough free space**) to make an unallocated part on the disk then you can either reformat that into ntfs or extend the windows partition to fill the empty space

most the time this will not cause any problems but it is a good idea to backup any important data as if something goes wrong during the process it will be lost

---

### Post by murderd2death on 2011-09-12
> **dave01945 said:**
> if you use a live cd/usb you can use gparted (**this is on the ubuntu live cd/usb**) to resize the ubuntu  partition (**as long as there is enough free space**) to make an unallocated part on the disk then you can either reformat that into ntfs or extend the windows partition to fill the empty space

most the time this will not cause any problems but it is a good idea to backup any important data as if something goes wrong during the process it will be lost

i have gparted right now, but i wont have access to the live cd until this afternoon, can i do it without the cd?

---

### Post by dave01945 on 2011-09-12
you cannot resize the ubuntu partition while it is in use thats why you need to use a live cd/usb because if the system is booted from the hard disk it will not let you resize it

---

### Post by Basher101 on 2011-09-12
also is the ubuntu partition INFRONT or AFTER your NTFS partitions? if it is after it you will have to move the partition which will take hours, depending on your partition size.

---

### Post by Mark Phelps on 2011-09-12
Three things you need to watch out for:

1) When you shrink the partition with GParted, do not be surprised if the now unallocated space is on the "right" side of the partition, leaving you with the arrangement of: 

Win7 OS partition -- Linux filesystem partition -- free space

This means you will NOT be able to combine the free space with the Win7 OS partition because the Linux filesystem partition is in the way.

You will have to "move" the Linux filesystem partition to the right to take up the free space -- but I haven't used GParted in a while, so I don't know if you can do that.

You should take a look at the Disk Utility and see if IT will allow you to move the Linux filesystem partition to the right.

2) Extended partition shrinkage.  If your Linux OS partition is inside an Extended partition, when you shrink the Linux partition, not only will you have to move IT to the right, you will have to shrink the Extended partition as well.  If you don't move the Linux OS partition to the right, you will not be able to shrink the Extended partition.

3) Win7 OS partition. To be safe, do NOT use GParted or the Disk Utility to expand the Win7 OS partition to take up the free space.  Instead, boot into Win7 and use the Disk Management utility to expand the partition.

---

### Post by murderd2death on 2011-09-12
> **Basher101 said:**
> also is the ubuntu partition INFRONT or AFTER your NTFS partitions? if it is after it you will have to move the partition which will take hours, depending on your partition size.

[this is my partition setup]("http://i.imgur.com/MEprm.png")

---

### Post by dave01945 on 2011-09-12
you should be able to shrink the ubuntu partition to the right to make space in-between **/dev/sda2** and **/dev/sda6** but as someone else mentioned this will take hours to complete then you can use windows to extended the windows partition if thats the one you want to extend

i'm sure someone will correct me if i'm wrong as i have only done this to primary partitions never extended partitions don't know if they will be any different

---

### Post by Basher101 on 2011-09-12
yep with this setup it will take hours and hours...how to do:

1. shrink ubuntu partition inside the extended partition
2. move the unallocated space out of the extended partition
3. extend the windows partition from inside windows after the unallocated space is between windows and the extended partition.

---

### Post by murderd2death on 2011-09-12
> **Basher101 said:**
> yep with this setup it will take hours and hours...how to do:

1. shrink ubuntu partition inside the extended partition
2. move the unallocated space out of the extended partition
3. extend the windows partition from inside windows after the unallocated space is between windows and the extended partition.

and this is all capable with a live cd? 

is the moving process going to be one i can use applications alongside it while its doing its thing?

---

### Post by oldfred on 2011-09-12
You do not want to do anything while partitions are getting reorganized.

If you do not have a lot of data in your Linux partition the shrink should not take too long.

But I suggest you do not combine the unallocated with your C: drive. Even many Windows users suggest a separate data partition so when you have to reinstall Windows your data does not have to be reinstalled. You of course still need backups.

The shared also reduces any issues of Ubuntu's NTFS driver writing directly into the Windows system (C: ) partition. Windows seems to not like a lot of activity by other systems. I have a shared NTFS with XP and that has worked without any real issue.

Previous posts have gone over most of the issues. If you want more info:
Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

---

