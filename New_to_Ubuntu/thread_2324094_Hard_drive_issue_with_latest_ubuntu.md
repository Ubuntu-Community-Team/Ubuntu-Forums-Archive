---
title: "Hard drive issue with latest ubuntu"
date: 2016-05-10
forum: New to Ubuntu
---

### Post by beba on 2016-05-10
Hi.

Ive been dabbling with ubuntu and various other linux distros over the years but never used one full time before, lately the ssd i have my windows installation on has been failing, yesterday i had to remove it and whack ubuntu on an emptty partition of one of my hard drives

my computer has 4 drives, so far only 3 are showing in ubuntu, if i go to the Disks application i can see the 4th drive, but it lists the main partition on it as "Unknown"
ive tried using the fdisk command and for the drive in question this is what it returns

Disk /dev/sdc: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 470A6597-9E4D-466A-B96A-2ADEBA06EED6


Device      Start        End    Sectors  Size Type
/dev/sdc1      34       2081       2048    1M Microsoft LDM metadata
/dev/sdc2    2082     262177     260096  127M Microsoft reserved
/dev/sdc3  262178 5860533134 5860270957  2.7T Microsoft basic data


Partition 1 does not start on physical sector boundary.
Partition 2 does not start on physical sector boundary.
Partition 3 does not start on physical sector boundary.



Im thinking the "Partition does not start on physical sector boundary" is the problem but im not sure how to fix it
can someone please offer a little advice so i can get my data back?

Cheers
beba

---

### Post by neu5eeCh on 2016-05-10
So wait... is the 4th drive the failed SSD?  Though you said you removed it? Does that mean you had 5 drives originally? And what do you mean by whack? Sorry if it seems like I'm asking the obvious...

---

### Post by oldfred on 2016-05-10
No, I think the issue is the LDM, which is dynamic partitions, somewhat like LVM is in Linux.

I have posted this many times and on MBR disks most of the time users have said it works, but never seen a LDM gpt drive.
 Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas/Symantec for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
From Linux view LDM
[http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from](http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from) 


 [http://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv](http://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv) 
   Used EASEUS Partition Master -  free version used to  include conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

---

### Post by yancek on 2016-05-10
Perhaps you could post which version of windows you are using as microsoft has been licensing their operating system for over 30 years?

Your output shows only one 'drive' with three partitions all of which are windows?  Are you confusing 'drive' with 'partition'?  When Linux users use the term 'drive', we are referring to an actual hard drive whereas in windows the terms are often used interchangeable which leads to a lot of confusion.  Also the drive/partition information you posted shows the hard drive as 'sdc' with three partitions.  In Linux, the first drive is generally referred to as sda, do you have other hard drives attached or that were attached?

And how exactly are you using Ubuntu as there is no sign of anything Linux in the output you posted?  Are you using a Live DVD?

What did you remove, the SSD?  Is the device with the output you posted just a data drive?

---

### Post by beba on 2016-05-10
> **VTPoet said:**
> So wait... is the 4th drive the failed SSD?  Though you said you removed it? Does that mean you had 5 drives originally? And what do you mean by whack? Sorry if it seems like I'm asking the obvious...

Yes, 5 drives total originally (including the SSD), now i have 4, none of the 4 drives still in the computer have any issues
edit: oh and forgot to mention, by whack i just meant install, sorry

> **yancek said:**
> Perhaps you could post which version of windows you are using as microsoft has been licensing their operating system for over 30 years?

Your output shows only one 'drive' with three partitions all of which are windows?  Are you confusing 'drive' with 'partition'?  When Linux users use the term 'drive', we are referring to an actual hard drive whereas in windows the terms are often used interchangeable which leads to a lot of confusion.  Also the drive/partition information you posted shows the hard drive as 'sdc' with three partitions.  In Linux, the first drive is generally referred to as sda, do you have other hard drives attached or that were attached?

And how exactly are you using Ubuntu as there is no sign of anything Linux in the output you posted?  Are you using a Live DVD?

What did you remove, the SSD?  Is the device with the output you posted just a data drive?

The output is only for the drive i have an issue with, there was much more output for each of my 4 drives (no im not confusing drive with partition), i just figured posting the relevant info would be better than posting all the output for all drives and partitions (4 drives total, each with a minimum of 3 partitions, i didnt wanna post more info than necessary, however if you need that info lemme know and ill gladly post it)
Yes its sdc. 
sda, sdb and sdd all work perfectly, all are attached

I was using windows 10 on my ssd, then after removing the ssd i installed ubuntu 16 on a partition on one of my drives (drive sdb i believe, though im at work atm so cant check til i get home a bit later), luckily i had a blank partition set up so it wasnt a problem to install ubuntu on it

> **oldfred said:**
> No, I think the issue is the LDM, which is dynamic partitions, somewhat like LVM is in Linux.

I have posted this many times and on MBR disks most of the time users have said it works, but never seen a LDM gpt drive.
 Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas/Symantec for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.


Thanks oldfred, ill be sure to check them out when i get home and let ya know how i go

@oldfred

you sir are a complete LEGEND
it was a dynamic to basic issue, just as you thought, i wasnt able to get too far with the links you gave me (though they did provide me with plenty of valuable info), eventually i just downloaded a disc image for minitool partition manager and ran that, was able to fix the problem quite quickly

thanks so much for your help

---

