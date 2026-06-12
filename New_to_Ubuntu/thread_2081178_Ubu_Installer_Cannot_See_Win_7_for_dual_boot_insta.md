---
title: "Ubu Installer Cannot See Win 7 for dual boot installation?"
date: 2012-11-06
forum: New to Ubuntu
---

### Post by mapes12 on 2012-11-06
Here's an intersting one. I have a PC with a 500GB. The disk is partioned from left to right like this:-

200MB Protected (I think this is a Win 7 "thing")
249GB NTFS partitioned with WIN 7 installed on it. Reported as the C: drive in Windows. The machine boots into Windows OK.
250GB Unallocated free space.

My objective is to install Ubu side by side with Win 7 but split the 249GB partiton 50/50 between Win and Ubu. I want to keep the unallocated space untouched.

I boot from the Live CD and tell it to install to the HDD. It then tells me that no other operating system is detected and wants to install Ubu to the entire drive. So, I go to the Advanced menu but it only sees my entire drive as /dev/sda. Nothing else. I run lshw and it can see /dev/sda (500GB) and also:-

*-volume:0  /dev/sda1
*-volume:1 UNCLAIMED Windows NTFS volume   264GB

How can I get the installer to understand that there is already an OS on the machine so that GRUB gets configured to dual boot :confused:

I'm sure I've done this before on other machines with XP installed and the installer could see the Win installation.

---

### Post by Mark Phelps on 2012-11-06
Whatever you do, do NOT use the Ubuntu installer to split the Win7 OS partition or shrink it.  Doing that risks corrupting the Win7 OS and rendering it unbootable.

Use ONLY the Win7 Disk Management utility to shrink the win7 OS partition.  

Then, leave the unallocated space empty and use the "something else" option in the Ubuntu installer to format it.

---

### Post by mapes12 on 2012-11-06
I'm making some progress. The Win 7 partition is sitting on a partition that has a **Hybrid MBR**. I can find tons of info about what one of these is and how I've ended up with it, but I can't find a solution for installing Ubu as a dual boot with Win 7. 

I've booted up the Win 7 installation DVD and run Bootrec.exe to see if I can change the Hybrid MBR to a standard MBR. I followed all the info on this [MS support page]("http://support.microsoft.com/kb/927392#method1") but still no luck. Win boots up fine but Ubu is still reporting all of /dev/sda as unallocated.

I've tried Boot Repair from the Live Ubu CD and that did no good either.

Nothing I've tried can change this Hybrid MBR to a standard that Ubu recognises.

Anyone got any ideas :confused:

---

### Post by mapes12 on 2012-11-06
Sorted! I used a CL utility called gdisk. It's on a range of freeware partitioning bootable CD's. I used Parted Magic. With gdisk there a a number of sub menus. Get to the recovery menu and then there is another sub menu of MBR tools. One of them rewrites the MBR. But this isn't the end of the solution. The gdisk action killed the Hybrid MBR but didn't install a new one. Win 7 wouldn't boot. So booted from the Win 7 DVD and went into the Sartup Repair utility. Startup Repair took ages but it figured out that a new MBR needed to be written, did the job and now all is well. Ubu can now see the Win 7 installation and the free space where it needs to go.

This has only taken all day so not bad compared to some PC nightmares  :P

---

### Post by oldfred on 2012-11-06
What is hybrid MBR? 

Post this from terminal in liveCD/USB:

sudo fdisk -lu

sudo parted /dev/sda unit s print

---

### Post by mapes12 on 2012-11-06
Hello Oldfred

Have a read of this: [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

---

### Post by oldfred on 2012-11-06
Familiar with that, just not seen it except in Macs, which I do not attempt to help with.
srs5694 used to be in the forums. And from him I gather you do not want hybrid gpt & MBR partitioning.

It may not have been a hybrid, but a gpt drive that had Windows then installed in MBR mode. Windows only overwrites the primary gpt partition table but not the backup gpt partition table.  Same author created fixparts for that type of issue.

---

