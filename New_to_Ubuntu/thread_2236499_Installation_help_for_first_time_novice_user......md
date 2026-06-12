---
title: "Installation help for first time novice user....."
date: 2014-07-27
forum: New to Ubuntu
---

### Post by bhuvan2 on 2014-07-27
Hello Guys,

I wanted to dual boot ubuntu on my windows laptop, so when i tried, the installer doesn't seem to recognize Windows 7 and also i don't see any partition which i have in my windows ecosystem, please any help will be much appreciated. Thanks

---

### Post by grahammechanical on 2014-07-27
Please take a screen shot of your the hard drive partition layout from Windows 7 and post it here. And supply the hardware specification of your machine. Look at the second image that you have provided. Look at the panel on the left of the screen (the launcher). That is showing three icons representing drives/partitions. Do you have more than one hard disk?

Another thing that you could do from the live session is open the Disks utility. What does that show you about your hard drives and their partitions?

Regards.

---

### Post by kc1di on 2014-07-27
Hi bhuvan2 and welcome to Ubuntu,

There is a problem in the installers partitioning on some machines with GPT /UEFI systems - Where it does not see the other partitions. 
in your case I believe you'll have to use a third party disk partitioner  to partition the disk and make room for Ubuntu ahead of time. 

First a couple question is this a Windows 7 or 8 install?  
2nd is it a GPT partion , UEFI (Secure boot) Raid or LVM? 

You may find[ this article]("https://help.ubuntu.com/community/WindowsDualBoot") helpful.
and also [this one ]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/798285")may hold a clue also.
good Luck

---

### Post by thibault3 on 2014-07-27
I used the partitioner of windows, best bet on correctly partitioning (I think). I love ubuntu but I used other software to make sure I left nothing to chance.
In a lot of how-to's they reccomend partitioning beforehand ESPECIALLY with UEFI.

---

### Post by Bucky Ball on 2014-07-27
Gparted does the job fine. You can boot from a LiveDVD/USB, 'Try Ubuntu', get to a desktop, launch Gparted and create the EXT4 partitions (and the 2Gb /swap) partition, then back to the desktop and hit the install icon.

When at partitioning during install, hit 'Something Else' and install directly to those partitions you created.

A basic, and example only, setup might be:

/ = 20Gb - where Ubuntu lives;
/home = large as you like - where your stuff lives;
/swap = 2Gb (unless you hibernate, then large as or bigger than installed RAM).

Ubuntu will need at least / and /swap.

* Just noticed your second screen shot where you have 'something else' marked. Yes, use that. You should see the Win partitions in there. They will be NTFS and if you are running EFI then you will have a small FAT partition there somewhere also. Just avoid anything NTFS when you are setting up the partitions/installing Ubuntu.

The not seeing Win bug is known and if you proceed can wipe the drive. So DON'T proceed, as you're not so far. Use 'Something Else'. ;)

---

