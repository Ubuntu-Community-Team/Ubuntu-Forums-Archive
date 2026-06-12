---
title: "Preinstalled Ubuntu 8.04 on Thinkpad R61i-"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by alexcckll on 2008-11-15
Hi folks, 

I know I may have mentioned this in General... but I'm still nervous.

I bought this Lenovo Thinkpad R61i-7650-EBG from Linux Emporium preinstalled with version 8.04.  Consequently, I do not know what tweaks, if any, were made to the machine.

Nor do I really care.

I *think* it uses integral Intel graphics, I *think* from lspci it uses a Broadcom Gigabit Ethernet controller, and Intel 4965 Wifi adapter.

I accepted updates up to 8.04.1... but have not accepted any updates from the beginning of October this year, as this was when the 2.6.24-21 kernel updates came out, along with related packages... and broke a lot of machines.

I am *new to Linux*.  It is also my sole machine.  I would NOT know how to get it up and running again if an update broke my machine - instead I would send it back to my vendor.

I purchased a Linux machine as it would be cheaper in the long run to be honest.

I use ans support XP at work - and support Lotus Notes at work.

What I need to know is - can anyone guarantee that this computer will work and reboot safely if I accept all recommended updates currently offered?

Has anyone tested and certified the latest patch releases against the Lenovo Thinkpad R61i 7650-EBG yet?

---

### Post by MasterSander on 2008-11-15
No one can guarantuee it 100% of course but I think it won't break anything, plus the gryb automatically creates a new entry for a new kernel and your old kernel entry is still there if something goes wrong.

---

### Post by mapes12 on 2008-11-15
Back up your system files ahead of the update. Heres how to do it: [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087) 

Then, if the update breaks anything just reinstall 8.04 to your system partition, unpack the tar file explained in the how to and you will be as you were before. If you have /home on a separate partition (highly recommended) then also exclude /home from the tar file i.e ```
--exclude=/home
``` added to the command to create the tar file.

Moving /home to its own partition is here: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by alexcckll on 2008-11-15
Slight problem.

I do not know how this machine was partitioned. I DID NOT INSTALL THE OPERATING SYSTEM,

It is currently a black box to me.  However, I *do* know about the necessity of keeping up to date with critical updates.

My vendor suggested unticking anything mentioning 2.6.24-21... but might this break something else?

All I really know how to do at the moment is go to Update Manager, click on Check, supply my password, and then click on Install.

If this is not properly QA'd... I don't want to brick my machine.

---

### Post by mapes12 on 2008-11-15
To check what partitions you have go to Terminal ```
sudo fdisk -l
```and post the output on this thread. Alternatively if you have an Ubuntu Live CD then boot your machine with it and run GParted which will give you a GUI of your partitions. You can also get a GParted Live CD direct from the home page here: [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Even if /home is not on its own partition the system backup how to I mentioned previously will also backup /home in the format that the OP has posted, so everything will be backed up for you.

If you ever need to restore your system for whatever reason you WILL need to know your partition configuration. So getting to grips with it now is a good opportunity.

I have an IBM Thinkpad T23 with all updates installed. The Linux kernel version you mentioned hasn't broken anything here.

The Linux Emporium is a good suppler of Linux kit. I have bought stuff from them myself and can only report a good experience.

---

### Post by InfectedWithDrew on 2008-11-15
> **mapes12 said:**
> To check what partitions you have go to Terminal ```
sudo fdisk -l
```and post the output on this thread. Alternatively if you have an Ubuntu Live CD then boot your machine with it and run GParted which will give you a GUI of your partitions. You can also get a GPareted Live CD direct from the home page here: [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Even if /home is not on its own partition the system back how to I mentioned previously will also backup /home in the format that the OP has posted, so everything will be backed up for.

If you ever need to restore your system for whatever reason you WILL need to know your partition configuration. So getting to grips with it now is a good opportunity.

I have an IBM Thinkpad T23 with all updates installed. The Linux kernel version you mentioned hasn't broken anything here.

The Linux Emporium is a good suppler of Linux kit. I have bought stuff from them myself and can only report a good experience.

To add to what this fellow said, you can also install GParted through Synaptic's Add/Remove menu.

Chances are, you have your drive of whatever size, let's say 500 GB.  And 497 GB of that is your ext2 partition, and you've got 2GB of swap, and the rest is junk that just occurs in hard drives.

---

### Post by alexcckll on 2008-11-15
alex@ubuntu:~$ sudo fdisk -l
[sudo] password for alex: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5836    46877638+  83  Linux
/dev/sda2            5837        6322     3903795   82  Linux swap / Solaris
/dev/sda3            6323       19457   105506887+  83  Linux
alex@ubuntu:~$

---

### Post by mapes12 on 2008-11-15
In English:

sda1 - this is your first partition with your system files on it, otherwise known as /root and where your system boots up from.

sda2 - This is your Swap partition i.e. extended memory space in case your system needs it.

sda3 - This is another Linux partition but I can't see how it's being used. It may be /home. The only way I know of telling is to have GParted look at it and post a screen shot. But don't do this > To add to what this fellow said, you can also install GParted through Synaptic's Add/Remove menu. because GParted will not report your active file system i.e. mounted partition on a working system. Run it from a CD as mentioned before.

The other way to check is simply to ask the guys at Linux Emporium.

---

### Post by alexcckll on 2008-11-15
From the boot messages (all text - a LOT easier to see what is going on - and how it came out of the box)... I would surmise that /dev/sda3 is the rest of my filesystem.

Thinking about it - I did dabble with SuSE 8 on my old Toshiba Satellite 230CX (HDD had died)... /dev/hda1 was /boot, and /dev/hda3 was /...

This would be similar?

---

### Post by ugm6hr on 2008-11-15
I hear that Linux Emporium are pretty good with support.

Why not just email them to ask if they are aware of any issues with your hardware and recent Ubuntu updates?

---

### Post by mapes12 on 2008-11-15
> From the boot messages (all text - a LOT easier to see what is going on - and how it came out of the box)... I would surmise that /dev/sda3 is the rest of my filesystem.

Thinking about it - I did dabble with SuSE 8 on my old Toshiba Satellite 230CX (HDD had died)... /dev/hda1 was /boot, and /dev/hda3 was /...

This would be similar?You could be right be certainty is required.

> I hear that Linux Emporium are pretty good with support.

Why not just email them to ask if they are aware of any issues with your hardware and recent Ubuntu updates?Agreed!

To finish this off. You will need to know what is installed on each partition. The reason for this is that in the unlikely event that Update Manager updates break you system then you need to have a method of restoring everything. Using the system backup how to mentioned before then all you would need to do is reinstall 8.04. BUT during the installation you will get to a section called "Partitioning". The default here is "Guided - Use entire disk". If you are trying to restore your system then this is not the preferred option. You need to select the last option "Manual" which will then ask you what you want to do with each partition. So, in your case you would select sda1, set the variable for it to be /(root) and to format it as ext3. Then for sda2 for this to be SWAP. And lastley, if sda3 is /home then select /home from the options but DON'T format it. This is on the assumption that sda3 is /home. If it isn't then just re configure accordingly.

By this point you will be back to a working system, but it will not be the same as the one you had lost previously including all the additional packages & applications you had before. So, you move the tar file you created before everything went pear shaped into your /root folder and execute the unpack command detailed in the how to. KeeePow! You have restored your system to the state it was before the upgrade. The whole process is similar to what "System Restore" does in windoze.

Hope this has been of assistance.

---

### Post by alexcckll on 2008-11-16
> **mapes12 said:**
> You could be right be certainty is required.

Agreed!

To finish this off. You will need to know what is installed on each partition. The reason for this is that in the unlikely event that Update Manager updates break you system then you need to have a method of restoring everything. Using the system backup how to mentioned before then all you would need to do is reinstall 8.04. BUT during the installation you will get to a section called "Partitioning". The default here is "Guided - Use entire disk". If you are trying to restore your system then this is not the preferred option. You need to select the last option "Manual" which will then ask you what you want to do with each partition. So, in your case you would select sda1, set the variable for it to be /(root) and to format it as ext3. Then for sda2 for this to be SWAP. And lastley, if sda3 is /home then select /home from the options but DON'T format it. This is on the assumption that sda3 is /home. If it isn't then just re configure accordingly.

By this point you will be back to a working system, but it will not be the same as the one you had lost previously including all the additional packages & applications you had before. So, you move the tar file you created before everything went pear shaped into your /root folder and execute the unpack command detailed in the how to. KeeePow! You have restored your system to the state it was before the upgrade. The whole process is similar to what "System Restore" does in windoze.

Hope this has been of assistance.
Pretty nervewracking, to be honest.

I suppose I'm used to corporate IT - where we have workstation builds and I'm following processes linked to already-built NAS restore processes (or restoring for a user means updating a service request that had been sent down).  I never got into TAR so far...

On the LiveCD front... I do remember reading somewhere that R61s weren't all that good with live CDs... 

Oh - I did go to System/Admin/Hardware Drivers, supplied my password, and on presenting me with something that might have looked somewhat like XP's Device Manager.. remained blank with the words "No proprietary drivers are in use on this system".

I closed it without making changes - I am ALWAYS nervous when elevating my permissions... what does that message mean?  

Not used to monolithic OSs...

---

### Post by october1917 on 2008-11-27
Hello my friend.

Could you post me your xorg.conf?

I have some troubles setting up good graphics for Debian Lenny.

Thank you in advance.

---

### Post by louieb on 2008-11-27
fdisk shows you have two ext3 partitions and a swap partition.

Just wondering  which partition is used for what. to find out 
1st  to find out how full they are and what the mount point is.
please post the output of 
```
df -h
```

I use partimage to take my backups before doing major updates. works great. [Howto: Backup with Partimage - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=287522")

---

