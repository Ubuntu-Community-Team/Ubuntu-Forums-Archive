---
title: "Should I dual boot or partition to run Ubuntu?"
date: 2013-06-12
forum: New to Ubuntu
---

### Post by MemoryMarc on 2013-06-12
I've heard you can run Ubuntu from a flashdrive.  I plan on doing a lot of work in the OS such as working with various file types, software development, etc.  Is it possible to save the files that I create onto the same flashdrive that is running the Ubuntu OS?  If so, should I invest in a relatively large drive or should I just partition my HDD?

Any suggestions would be great, thanks.

-M

---

### Post by Mark Phelps on 2013-06-12
The flashdrive install is going to be slower than a hard drive install.  It might be close to the same speed if you are able to lay your hands on one of the new super speed flash drives, but since I can't afford one of them, I've not tried it.

As to dual-boot, what are you running as an OS at present?

---

### Post by MemoryMarc on 2013-06-14
Thanks for the reply. I'm running Windows 7 currently and would like to run both on a daily basis.  I'll be running W7 for schools stuff and learning Ubuntu in my spare time so a one time install won't be an issue.

-M

---

### Post by cincinnatus13 on 2013-06-14
Dual boot without question. Simple, kind of hard to screw up anything with it nowadays. Just defrag Windows, make a (or two) new partition(s), and throw Ubuntu on it. I recommend keeping / and /home as two separate partitions.

---

### Post by NikTh on 2013-06-14
> **cincinnatus13 said:**
>  Simple, kind of hard to screw up anything with it nowadays. 
Agreed. The installer is simple and clear. 
But if you stuck somewhere or any problem occur, then post here before you proceed. You can open Firefox and post here even during installation procedure. 

As for the USB installation.. yes it is slow. Even on USB3 is slower than HDD. (but better than USB2). I prefer a USB live with persistence space rather than USB full installation. 
See this answer for more info => [http://ubuntuforums.org/showthread.php?t=2076102&p=12317425#post12317425](http://ubuntuforums.org/showthread.php?t=2076102&p=12317425#post12317425)

Thanks

---

### Post by Mark Phelps on 2013-06-14
Since you're serious about dual-booting with Win7, and appear to need to be able to still use Win7 afterward, be sure to read through the ENTIRE post below -- before you try the dual-boot installation:

You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by MemoryMarc on 2013-06-18
Thanks for the info, I'll keep this thread updated once I begin
-M

---

