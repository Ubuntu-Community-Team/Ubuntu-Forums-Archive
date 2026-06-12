---
title: "install ubuntu to dual boot with Win.7 64bit 128gb sdd"
date: 2013-05-26
forum: New to Ubuntu
---

### Post by arranskye on 2013-05-26
Hi  having done much research on these forums i have found many different opinions on how to install. I have previously messed up twice, once corrupting the MBR so windows could not boot and once wiping Win 7 from the HDD completely. I am installing a new SDD and hope to get it right this time.

Install win 7 first. Install Ubuntu 12.04LTS using windows installer for ubuntu appears to be the most straightforward way.  Chose Ubuntu 12.4 LTS for its long term support and because it can use the windows installer as opposed to wupi which I understand should be avoided.

Is this the best way to approach installing to dual boot please.

I have not used 12.4LTS so I hope I like it. I like 12.10 better than 13.04.

hope i got the terminology and distros correct as i feel enough of an idiot as it is.   :confused:  thanks

---

### Post by Paqman on 2013-05-26
> **arranskye said:**
> Chose Ubuntu 12.4 LTS for its long term support and because it can use the windows installer as opposed to wupi which I understand should be avoided.


I suspect the "windows installer" you're talking about actually is Wubi (**W**indows **Ub**untu **I**nstaller)

Wubi is a perfectly good way to install, especially if you're not 100% sure what you're doing. It can be a little troublesome down the road, but it's a good way to dip your toe in the water. If you want a more robust solution then you should just use the normal installer (ie: burn the image to a disk or USB and boot from it), but if that's given you trouble then Wubi is definitely an option.

---

### Post by newb85 on 2013-05-26
If you do use Wubi/the Windows Installer, be careful about how you describe your setup down the road.  To many "dual-boot" means a traditional install.

You shouldn't feel like an idiot.  There's a learning curve to Ubuntu, and some resources available provide information a little too selectively.

---

### Post by arranskye on 2013-05-26
hi Guys, Thanks for quick response.  By normal installer do you mean the desktop install icon on 12.10 & 13.04.
This is what I used previously and had problems with.  My own lack of knowledge & experience. I think I should have unmounted the existing windows drive.  I knew from previous attempts that it was better to partition with gparted but really not too sure where I went wrong from there.

Also what is the main difference between ubuntu. 12.4lts & 12.10
 

I have been running ubuntu 13.4 from a disk for the past week but I intended to get a 12.4lts disk to install. 


Is this the same as "(burn the image from a disk or usb & boot from it)" please . 

Sorry newb85, your are very kind but what an idiot not to realize what the letters W.U.B.I. stood for. got to stop assuming that every linux word & phrase is a foreign language and take a much more logical and common sense approach.

Again much sincere thanks for your help.

---

### Post by newb85 on 2013-05-27
Yes, the normal installer, traditional install, and "burn the image from a disk or usb & boot from it" are one and the same.  They all mean using the .iso file to create a bootable DVD or USB (or CD for older releases of Ubuntu) and then booting from that.

12.10 is the only release I haven't installed since I started Ubuntu with 9.04.  This was partly due to community reception of 12.10 (it had more kinks to work out when released than most) and some major life events (If you could track my activity on the forums, you would notice a dead spot).  So, I can't speak to features, but I can point out that 12.10 hits End-of-Life in April 2014 (18 months from release) whereas 12.04 doesn't hit EOL until April 2017 (5 years from release).  The general recommendation is that you install either the latest release or the latest LTS release.

Specifically, what is it you like about 12.10 over 13.04?

---

### Post by zemega on 2013-05-27
12.04 lives longer than 13.04. There's talk to port back Unity 7 (used in 13.04) into 12.04. That's all i guess? Honestly you can just skip 12.10. 13.04 is fast, Unity 7 is really good over the previous version.

If you use the option install inside Windows, isn't that WUBI? but I tought WUBI was not available for 13.04, but I got the 'install inside Windows' option using 13.04 ISO.

To dual boot. Install Windows 7 first (Its easier this way). Reduce Windows 7 partition size so you can install Ubuntu. Boot into live installer. Use gparted to make the partitions, that depends on how you want it. A primary partition for all and an extended partition for swap, or seperate partitions for root and home. Select something else at the option. Select the partition you want to install '/' (and separate partition for '/home' if you wish). At the bootloader part, select 'sda', do not select 'sda1' that has the mark Windows loader. If you select sda1, you will corrupt Windows 7 loader. While Ubuntu usually just install / and /home in the same partition, advance users prefer separate for various reasons, particularly security and easy backup.

On the other hand, did you try updating your grub?

---

### Post by Mark Phelps on 2013-05-27
WUBI is being phased out -- and is already NOT available for 13.04.  So, don't get used to using it for the long haul.

Partitioning Win7 setup using GParted is a BAD idea, as that risks corrupting Win7 and rendering it unbootable.

IF you are serious about doing dual-boot NOT using Wubi then read through the details below BEFORE you do anything else ...

You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by Mark Phelps on 2013-05-27
Dupe -- please remove

---

### Post by newb85 on 2013-05-27
> **Mark Phelps said:**
> Partitioning Win7 setup using GParted is a BAD idea, as that risks corrupting Win7 and rendering it unbootable.

I'm not doubting that point.  However, I've always had trouble shrinking the Windows partition within Windows.  It won't let me, and I wouldn't expect it to.  Ubuntu behaves the same way.  (The partition has to be mounted to run the system, and it can't be altered while mounted.)

---

