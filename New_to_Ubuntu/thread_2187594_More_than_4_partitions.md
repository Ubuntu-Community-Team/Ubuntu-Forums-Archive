---
title: "More than 4 partitions?"
date: 2013-11-12
forum: New to Ubuntu
---

### Post by fwrun2011 on 2013-11-12
Hi;
Bran-new user to Ubuntu 12.04 LTS. I created dual-boot with Windows 7 X64. When I was creating the new partition for Ubuntu (using Gparted) I was not allowed to create more than 4 partitions.
My problem is this:
Drive is 1TB.
I have three NTFS partitions: 390GB, and 150GB, and the small one for Windows loader is 100MB.
I created one ext4 partition for Ubuntu.
I have 342GB unallocates space left.

I would have liked to create another partition, preferably NTFS so I can access it from both Windows and Ubuntu, but with the 4 partition limit, I suppose I will have to resize the 150GB part to fill the remaining space?
That is really not a problem, but I like to keep separate partitions for various reasons.
Could I perhaps get rid of the 100MB NTFS partition and move the Windows loader to the main Windows part - without having to re-install Windows?

Thanks for your help.

FW

---

### Post by Bashing-om on 2013-11-12
fwrun2011; Hi ! Welcome to the forum.

Do not mess with Window's boot code. 
One solution is to delete what you have made for the ubuntu partition(primary)... and then make that space "unallocated" Ok ? now what you do is when you make this next partition, using most of all that unallocated space, make it as an "extended" partition. Now within this 4th partition(extended) one may make as many logical partitions as one needs .. say ubuntu and ubuntu's swap partition - the install wizard will take care of these little details.
So, what you have is the original 3 primary partitions plus and extended partition that counts as the 4th primary partition, and in this extended partition one may have as many logical partitions as desired.

ubuntu will be quite happy to install into the extended partition.

[INDENT][INDENT]many roads can lead to an install
[/INDENT][/INDENT]

---

### Post by fantab on 2013-11-12
The Legacy 'msdos' partition table has this limitation of ONLY four Primary Partitions. To overcome this we use an EXTENDED Partition, which is a Primary partition but actually acts as a container for LOGICAL Partitions.
Do as Bashing-om suggests.... 
In effect you will be deleting a partition so BACK UP ALL IMPORTANT DATA ON THE PARTITION, and also on other partitions first.

OR

Use [MINI TOOL Partition Wizard]("http://www.partitionwizard.com/convertpartition/primary-or-extended-partition.html") to convert the Primary Partition to Extended. 

BACK UP ALL IMPORTANT DATA, preferably to an external device.

Good Luck.

---

### Post by fwrun2011 on 2013-11-13
Thanks guys;
Since I already had Ubuntu installed, and didn't want to bother with changing its partition, I decided to extend the 150GB NTFS partition into the unallocated space. So I've got a huge amount of storage for files now. That's good. I need to get past the desire to have separate smaller partitions on the large HDD. This goes way back to the days when large partitions were a problem.
I was also not sure whether Ubuntu would run from an extended partition, but now, thanks to you, I know that it will.

One note: When I ran GParted from within Ubuntu to resize the partition, it took a very long time, compared to the time it would have taken had I booted back into Windows and done it from there. Why is that? Is GParted just more thorough - does it check the disk as it goes, or what?

FW

---

### Post by Bucky Ball on 2013-11-13
You should defrag NTFS and Win partition before shrinking/expanding.

If you create a large extended partition you can have as many smaller logical drives (effectively partitions) inside that as you want.

---

### Post by fwrun2011 on 2013-11-13
Perhaps I should do that, then re-install Ubuntu - since I only did the install yesterday, and I haven't done anything with it that I need to save.

---

### Post by Bucky Ball on 2013-11-14
Perhaps. Three Win partitions and the rest of the drive (free space) one large extended partitions in which to install the Ubuntu /, /swap partitions (and a separate /home partition if you wish).

---

### Post by fwrun2011 on 2013-11-16
Here's an interesting piece of info:
I was having trouble with Windows 7 - Windows Failed to Start messages were occurring occasionally. People in one of the Windows forums suggested that I move the Windows boot files to the system drive, and get rid of the 100MB partition.
I was pointed to a website where they walked me through this procedure, using EasyBCD, and a partition utility. I followed all the instructions, and now have Windows 7 (same install as before - did not have to re-install) and ubuntu 12.04 coexisting peacefully on the same computer.
What is interesting is that after re-installing Ubuntu - and choosing the first option for install this time (the option that keeps Windows 7 but erases the old Ubuntu install) - when I first installed Ubuntu, I chose the "something else" method, and installed Ubuntu on its own 48G partition which I had created. I didn't have a swap partition for that install - but after the 2nd Ubuntu install, a 7.8G (I have 8G RAM) swap partition was automatically created, taking the 7.8G from the 48G ext4 partition I had already set up for the 1st install of Ubuntu.
I probably should have used this method in the first place, but the article I was reading suggested not to create a swap partition, but to create only a swap file on the Ubuntu partition. 

So I've got a total of 4 primary partitions on the drive where Ubuntu and Windows are installed. It appears that everything is working now.

FW

---

### Post by Bucky Ball on 2013-11-16
Please mark thread as solved by using the instructions in my signature. Thanks. ;)

---

