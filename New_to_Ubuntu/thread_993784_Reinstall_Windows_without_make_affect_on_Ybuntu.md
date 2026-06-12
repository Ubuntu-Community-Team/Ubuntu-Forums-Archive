---
title: "Reinstall Windows without make affect on Ybuntu"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by Goutam Roy on 2008-11-26
I am a new user of Ubuntu and now using both Windows xp and Ubuntu 8.10. Ubuntu is working fine though I am getting some problems on Wisdows. So, I want to uninstall the Windows first and format C drive and then reinstall it. If I do this, will I get any problem regarding Ubuntu as I installed it from Windows? And if I will not get any problem, then will I be able to uninstall Ubuntu from Add/Remove programme, if needed?

---

### Post by wardrich on 2008-11-26
Assuming you format the NTFS partition and not the EXT one (which I think will show up in the xp installer as "unknown") you should be fine.  The only issue I can think of is that god-awful bootloader that comes with windows.  It'll probably override GRUB.  Getting this re-installed shouldn't be a hassle.  I've never had to do it, myself but I'm sure there's something on the Ubuntu Live CD that will fix the problem in a jiffy.

As for uninstalling Ubuntu from "add/remove".  You won't be able to do that for many reasons... namely the fact that Ubuntu is a Unix-based operating system that lies on a partition on your hard drive using a file system that Windows still can't recognize, as opposed to a simple win32 program that is executed from within windows. 

Does that make sense?

---

### Post by bobnutfield on 2008-11-26
> **Goutam Roy said:**
> I am a new user of Ubuntu and now using both Windows xp and Ubuntu 8.10. Ubuntu is working fine though I am getting some problems on Wisdows. So, I want to uninstall the Windows first and format C drive and then reinstall it. If I do this, will I get any problem regarding Ubuntu as I installed it from Windows? And if I will not get any problem, then will I be able to uninstall Ubuntu from Add/Remove programme, if needed?

If I understand correctly, you are running Ubuntu inside Widows using Wubi.  If that is correct, then you do not have a separate partition for Ubuntu and you will wipe Ubuntu as well if you re-install Windows.

---

### Post by wardrich on 2008-11-26
> **bobnutfield said:**
> If I understand correctly, you are running Ubuntu inside Widows using Wubi.  If that is correct, then you do not have a separate partition for Ubuntu and you will wipe Ubuntu as well if you re-install Windows.

If he's right, please disregard my post.  I've never really looked at (or read about Wubi).  Sorry.

---

### Post by Goutam Roy on 2008-11-26
Thanks Wardrich and Bob. Actually, I have to format the C drive and then install the windows and other softwares again. What I understand if I do this, then I would not be able to uninstall ubuntu from windows (ubuntu is installed at F drive). If so, how can I uninstall ubuntu later?

Need help in another issue.
After installing ubuntu, I have lost around 4 GB space from the disk. How can I get back this space?

Thank all of you for kind help.

---

### Post by bobnutfield on 2008-11-26
My recommendation would be to backup any data you want to save, to a USB disk, for instance.  Then you can use the LiveCD to open the partition editor ((System>Adminstration>Partition Editor), and set up your disk for a dual boot.  You would first delete all existing partitions, then you must decide how much space you want to allocate to each OS.  You would then format the first partition as NTFS to prepare it for Windows, then the second partition for Ubuntu as ext3.  I would also recommend a separate partition for your /home directory so that future upgrades/re-installs of Ubuntu would leave your home directory intact.  A sample (only a sample) allocated 100gb disk is as follows:

40GB  --  NTFS (for Windows)
15GB  --  Ubuntu root files
43GB  --  Ubuntu /home
2GB   --  Swap (for Ubuntu)

This is only a sample, and the swap partition does not have to be that large, depending on the amount of memory you have.  This should retrieve any missing hard drive space as well.  Remember to install Windows first because if you install it second it will install its own boot record and wipe your grub installation from the MBR.

---

### Post by wardrich on 2008-11-26
This is kinda where we run into where the topic can branch off.  If you're running Wubi, then the 4gigs is probably like a virtual disc that Wubi creates in order to store Ubuntu.  As I mentioned before, I've never used or read into it, so I'm far from an expert.  However, if you are using Wubi and you uninstall it, you should be able to regain that 4gb of space back.

If you're NOT using wubi, then the 4 gigs of space disappeared because you probably shrank your NTFS partition down to make room for Linux, which is probably not the case, however if it is, then it means that your Ubuntu partition is totally separate from your Windows one.  You'd get rid of Ubuntu just like you'd get rid of Windows.  In fact, you can actually do it with the windows CD while you're re-formatting.  Just get rid of both your windows partition and the one that Ubuntu is on (they'll both show up in the list of partitions).  If they're the only two partitions you have, then just get rid of 'em both.  If you have another partition for data, then just go by the sizes of each partition to determine which one is your XP Partition, which one is your Ubuntu partition, and which one is your Data partition, and get rid of the appropriate two.

---

