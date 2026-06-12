---
title: "[SOLVED] Duel Booting with XP"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by Fishbot4000 on 2008-05-19
I know that this question must have been asked several thousand times, but this *is* the beginners forum, and I *am* a beginner, so I figure there's no harm...

I currently have windows XP, and just finished downloading Ubuntu: Hardy Heron. Now, my current hard drive is only 40gb and completely full. What I want to do is purchase a second hard drive to run Ubuntu, while leaving my current hard drive untouched. I've read many of the tutorials that others have posted, but none of them seem to fit this problem exactly. Quite frankly, I have no idea how to go about doing this because, well, I'm 112% new to linux.

Does anyone have solutions?
(again, sorry for the - most likely - repeated noob post)

---

### Post by wolfen69 on 2008-05-19
install new hard drive. when installing ubuntu, when you get to the part where you have to choose where to install ubuntu, just choose the new drive. that's it. when you are all done and reboot, you will be given a choice of which OS to use.

---

### Post by overdrank on 2008-05-19
> **Fishbot4000 said:**
> I know that this question must have been asked several thousand times, but this *is* the beginners forum, and I *am* a beginner, so I figure there's no harm...

I currently have windows XP, and just finished downloading Ubuntu: Hardy Heron. Now, my current hard drive is only 40gb and completely full. What I want to do is purchase a second hard drive to run Ubuntu, while leaving my current hard drive untouched. I've read many of the tutorials that others have posted, but none of them seem to fit this problem exactly. Quite frankly, I have no idea how to go about doing this because, well, I'm 112% new to linux.

Does anyone have solutions?
(again, sorry for the - most likely - repeated noob post)

HI and welcome, installing on a second drive is basically the same. You will need to back up all your data as there is always a chance for a wrong click and gone. You also can always just run the live cd and verify that there will be no issues with your hardware.

---

### Post by ZabiGG on 2008-05-19
And since you're so new to Ubuntu (and welcome to the community, btw), you might benefit from familiarizing yourself with the basics. Just click on the links to starter info and how to more easily get help on the forums in my signature.

Cheers,

Z.

---

### Post by Kevbert on 2008-05-19
Make two partitions on the new drive.  One can be formated NTFS for windows, the other FAT32 (it's not important). You can do this through XP.  Your 'FAT32' drive you want to use for Ubuntu and you want to make it at least 20Gb.  Use the NTFS drive for XP.
When you install Ubuntu you want to use the second (FAT32) partition and the  Manual partitioning option.   Set the Swap file for at least 2 x your RAM memory and the rest for the Ubuntu system formatted ext3 and mount point will be /
So if you have a new 100Gb you could have an NTFS (XP) drive of 50Gb, Ubuntu   ext3 48Gb system with 2Gb swap file (assuming that you have 1Gb of RAM x2 = 2Gb).
Ubuntu will generate a bootloader so that you can start Windows or Hardy Heron when you switch on the PC.

---

### Post by Fishbot4000 on 2008-05-19
Wow! Thanks for the quick responses!

On most other forums I usually just get responses like "Grow sum brainz n00b! LAWLZ!"

Anywho, thanks for the advice! I think I'm going to like this Linux community thing...

---

### Post by om1 on 2008-05-19
yes it is really that simple but if you run into any problems just post them.... remember to back up your important data before doing anything though because strange things happen.

---

### Post by Fishbot4000 on 2008-05-19
> **Kevbert said:**
> Make two partitions on the new drive.  One can be formated NTFS for windows, the other FAT32 (it's not important). You can do this through XP.  Your 'FAT32' drive you want to use for Ubuntu and you want to make it at least 20Gb.  Use the NTFS drive for XP.
When you install Ubuntu you want to use the second (FAT32) partition and the  Manual partitioning option.   Set the Swap file for at least 2 x your RAM memory and the rest for the Ubuntu system formatted ext3 and mount point will be /
So if you have a new 100Gb you could have an NTFS (XP) drive of 50Gb, Ubuntu   ext3 48Gb system with 2Gb swap file (assuming that you have 1Gb of RAM x2 = 2Gb).
Ubuntu will generate a bootloader so that you can start Windows or Hardy Heron when you switch on the PC.

Haha, I'm not sure I quite understand what you're talking about, but I'll save a copy of this post and research it a little. Perhaps one day I'll look back and think "oh, of course. How could I have NOT known what he was talking about."

Also, I forgot to thank ZabiGG for the very helpful links! Thanks again!

---

### Post by CloudFX on 2008-05-19
Also have a look here:
[https://help.ubuntu.com/8.04/switching/first-steps.html#dual-boot](https://help.ubuntu.com/8.04/switching/first-steps.html#dual-boot)

---

### Post by ZabiGG on 2008-05-19
> **Kevbert said:**
> Make two partitions on the new drive.  One can be formated NTFS for windows, the other FAT32 (it's not important). You can do this through XP.  Your 'FAT32' drive you want to use for Ubuntu and you want to make it at least 20Gb.  Use the NTFS drive for XP.
When you install Ubuntu you want to use the second (FAT32) partition and the  Manual partitioning option.   Set the Swap file for at least 2 x your RAM memory and the rest for the Ubuntu system formatted ext3 and mount point will be /
So if you have a new 100Gb you could have an NTFS (XP) drive of 50Gb, Ubuntu   ext3 48Gb system with 2Gb swap file (assuming that you have 1Gb of RAM x2 = 2Gb).
Ubuntu will generate a bootloader so that you can start Windows or Hardy Heron when you switch on the PC.

Aww... I'm a sucker for plain language explanations. Let me give this one a try:

You should make two partitions (two reserved special sections) on your new disk. Then you can format them in NTSF and FAT32 (these are disk formats used respectively by Vista and XP). There is an application in XP which lets you partition and format the disk. 

You want to set aside the FAT32 section of your disk for Ubuntu, and plan ahead when you partition: dedicate at least 20 GB worth of disk space to the FAT32 partition. XP should be installed on the NTSF -- why not FAT32, it thought it was native to XP, but what do I know... I'm just the cheerleader -- side of the disk. When you install Ubuntu, there will be a point when the system will ask you to partition and choose the format for your disk. At that time, the system will also ask you to create a "swap" file (virtual memory space). You should set it to at least twice the actual RAM in your computer. The rest of the FAT32 side of the disk will be converted to a linux friendly format, "ext3", and the equivalent of your C: drive will be / (called root) in Ubuntu.

This means that, if you have a new 100 GB drive, you can set up one 50 GB NTFS (XP) disk section, one 48 GB ext3 section for Ubuntu, and a 2Gb swap file (assuming that you have 1Gb of RAM).

Ubuntu will generate a bootloader (a loading screen on computer start-up) so that you can load either Windows or Hardy Heron when you open it.

But read the basics, it will all become much clearer... lol.

Cheers,

Z.

---

