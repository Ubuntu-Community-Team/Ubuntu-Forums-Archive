---
title: "Linux partition misaligned?"
date: 2011-10-18
forum: New to Ubuntu
---

### Post by cozumel on 2011-10-18
Hi,

I am totally new to Linux, so please be gentle with me!;)

I have installed 11.10 x64 alongside Windows 7 x64

My Hard Drive is a Western Digital Scorpio WD5000BPKT-75PK4T0

When I look at my partitions through disk utility that came with ubuntu and click on the Linux partition it says:
"**WARNING**: The partition is misaligned by 1024 bytes. This may result in very poor performance.  Repartitioning is suggested."

Does this mean I should delete the partition, resize and reinstall?

Thanks for your help?  (Sorry to be such a noob lol)

---

### Post by Bmonsterboy on 2011-10-18
Hey don't be so harsh on yourself. Everyone had to be a beginner once too :)
This might help: [http://ubuntuforums.org/showthread.php?t=1635018]("http://ubuntuforums.org/showthread.php?t=1635018")

---

### Post by westie457 on 2011-10-18
Hello and welcome to the Forum.

Before doing anything drastic and time consuming take a look at this thread and the links within it. [http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018) 
A lot of reading and information to digest.

Reformatting and re-installing will work however that is usually the 'when all else fails' option.

---

### Post by cozumel on 2011-10-18
Thanks gentlemen (or ladies) for your snappy replies and link(s).

Okay, just checked and my disk is Advanced Format (oh joy)

I'll download paragon alignment tool and then hopefully realign and validate correct alignment.

I'll post back if I am successful or have any further problems 

Thanks again guys (or gals) :D

---

### Post by mastablasta on 2011-10-18
gparted should have done the alignment. Is this still not done automaticly by it??!?!

---

### Post by cozumel on 2011-10-18
> **mastablasta said:**
> gparted should have done the alignment. Is this still not done automaticly by it??!?!I used gparted via the terminal from the livecd 11.10 to resize original partitions and create new partitions for Ubuntu.  So, it is either not automated or I did something wrong..

---

### Post by mastablasta on 2011-10-18
hmm i don't have the ubuntu near me now, so i am hoping someone will explain or reply to this. i somehow understoong this is done in gparted. 
 
Also you used gparted to shrink windows partition? then consider yourself lucky. oherwise this is better done with windows disk manager, as windows partition and gparted mix is not always a sucess. it is most of the time, but now always.

---

### Post by cozumel on 2011-10-18
> **mastablasta said:**
> Also you used gparted to shrink windows partition? then consider yourself lucky. oherwise this is better done with windows disk manager, as windows partition and gparted mix is not always a sucess. it is most of the time, but now always.I read that in various places/forums/sites.  I chose to ignore and use gparted as the whole point is to learn.  If I stick to using using Windows programs then I don't gain knowledge.  Basically thought to myself "what the heck.  Use linux to partition" lol

I did create image of win7 installation and backup important files first though

---

### Post by cozumel on 2011-10-18
Okay.

So I ran both Paragon Alignment Utility (PAT) and Dells Advance Format Detection Utility (AFDU), both from within Win7.  They both say all partitions are correctly aligned.  But Linux disagrees.

Any ideas please?

---

### Post by cozumel on 2011-10-18
Here is the output from "sudo fdisk -lu" and shows what Linux sees.

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x07f2837e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   949430271   474611712    7  HPFS/NTFS/exFAT
/dev/sda3       949432318   976771071    13669377    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sda5       949432320   968599551     9583616   83  Linux
/dev/sda6       968601600   976771071     4084736   82  Linux swap / Solaris
```

Actually, think I'll reboot into livecd and see if I can adjust partition size with gparted

---

### Post by oldfred on 2011-10-18
If all the starts of your partitions can be divided by 8 then you do not have a problem.

srs5694's to show 8 sector alignment post #9
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
$ sudo parted /dev/sda unit s print

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of RAID arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)

---

### Post by cozumel on 2011-10-18
Thanks oldfred.  I worked out a while ago about the start point having to be a multiple of 8.  Had my calculator out and new where I want it to begin.  Just don't know how to create the partition correctly aligned.

Since my last post I deleted Linux partitions with gparted and reduced the size of Windows partition.

I then manually created a knew extended partition with gparted.  First time align with MiB and misaligned so deleted.  Then align with cylinders and misaligned so deleted.  Then align with option 'none' and I got a multiple of 8. Great! :)

Then tried to install with live disk and paused install when asks me to input username etc.  Checked again with fdisk now the installer has created logical partitions and my extended partition has slightly resized and is no longer aligned. "Partition 3 does not start on physical sector boundary"

So, I'm back to where I started lol.

If it comes down to it, Ill wipe Windows, Linux and reformat the lot.  But I would prefer to learn what I am doing wrong as it obviously me doing to much of a noob with Linux and doing it all wrong.

Any suggestions please how to get my magical multiple of 8 pls :D

If anyone could walk me through it would really be appreciate as this is way beyond my current knowledge (but I'm eager to learn and am willing student)

---

### Post by oldfred on 2011-10-18
If partition 3 is your extended partition then it is not important. 

Is errors sector boundry or cylinder. Old fdisk still refers to cylinders even though cylinders have not been used for years (Since LBA  with drives over 8GB).

---

### Post by lobos marinos on 2011-10-18
deleted

---

### Post by cozumel on 2011-10-20
Hi, Partition 3  is the extended partion and is marked on Linux as misaligned.  Partions 4 & 5 are the linux system and swap, they are correctly aligned.

Are you saying that the only important factor is to have the logical partitions aligned correctly with the physical sector edge as they are the partitions that hold (store) the data?  Are you also saying because the extended partition does not actually hold the data, aligning is irrelevant?

If you can confirm both of these questions then I can mark as solved.

Thanks again for help.

---

### Post by oldfred on 2011-10-20
You do not write in the extended partition but the logical inside it, so only the logicals have to be aligned.

Even a small boot partition that you almost always just read from does not have to be aligned. It is the writes that you have to worry about.

I prefer to use gpt as then all partitions are primary, but in BIOS mode you cannot use gpt with Windows. So I have several drives, some still MBR and some gpt.

---

### Post by cozumel on 2011-10-20
Thanks.  Marked as solved!! :)

---

