---
title: "Windows 7 Dual Boot"
date: 2013-02-22
forum: New to Ubuntu
---

### Post by whyaname on 2013-02-22
Hey all,

I am an absolute beginner to this Linux stuff and had a couple of questions. I have been using the Live USB for a couple of months now and am finally confident enough to install Ubuntu on to my laptop but at the same time need Windows for essential programs like MATLAB and others for my college.

I read through the site on how to install Ubuntu but it still seemed confusing to me and I don't want to take any chances since I have a university laptop. My main questions are :
1. How do I partition the hard drive (I have a C drive and a D drive, can I install Ubuntu by de-allocating some space from the D drive or does it have to be the C one)?
2. What is this mount point and bootloader things? These have me the most confused and scared since the bootloader thing seems very important not to mess up.

Thank You for your help.

---

### Post by cool110 on 2013-02-22
First you need a single section of free space. Assuming C and D are both on the same physical drive it won't matter which one you shrink, if you shrink both you will need to move one of the partitions or use the smaller space for swap.
If you don't use a separate /home partition you can just leave the bootloader and mount points at the defaults.

---

### Post by Mark Phelps on 2013-02-22
Sorry ... but it matters VERY MUCH which one you shrink -- as shrinking the OS partition with GParted can result in corrupting the Win7 boot loader and rendering it unbootable.

Please read through the material below BEFORE you jump into dual-booting with Win7:

You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by whyaname on 2013-02-22
> **Mark Phelps said:**
> Sorry ... but it matters VERY MUCH which one you shrink -- as shrinking the OS partition with GParted can result in corrupting the Win7 boot loader and rendering it unbootable.

Please read through the material below BEFORE you jump into dual-booting with Win7:

You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.
I have only two partitions looking through the Disk Management Utility (C and D). Can i de-allocate space from the D drive (its the larger of the two) for Ubuntu (along the lines of 40 gb or so)? I already have a repair disk for my system in its current state.

---

### Post by audiomick on 2013-02-22
> **whyaname said:**
> I have only two partitions looking through the Disk Management Utility (C and D).

This is a bit unusual for a Win7 install; very often there are indeed 4 as Mark Phelps mentioned.

However: I think it is fair to assume that the D: partition is a data partition. That is the one I would shrink. I would then create an extended partition for the Linux install. You can put all of it on logical partitions without a problem, and having an extended partition established leaves you flexible if you need to add another partition in the future (e.g. you become so Linux fixated that you just have to install another variety... ;) ).

DO follow Mark's advice about doing the work on the Windows partition with the windows tool. I have not had any trouble to back up my views, but it just seems logical to me: Microsoft provides a tool to work on the partitions which have Microsoft format, so why not use it?

Further to that, do a de-frag before you start. No, wait on: **do a backup before you start**. Partitioning work is quite safe, but there is always a minimal risk involved (e.g. power failure half-way through...) so back up anything important before you do anything else. Then...

Do some housework. You need some space, so go through your files and chuck out anything you don't need anymore. Then do a de-fragmentation. I have read that if the machine has seen a lot of work, it can help to do this twice. It can take a while though, so it is up to you, but do it at least once.

Then use the windows tool to shrink the partition you have settled on.I would suggest leaving the empty space at the end of the drive rather than in the middle. I don't know for sure if there is a good reason for that other than that it is neater, but that is good enough for me.

Then start into Windows a couple of times to let it have a chance to do any disk repair stuff it might want to do.

This should leave you with a machine with a happy Win7 install on it and a bit of free space at the end of your drive. You can now go on to the linux install. I personally would boot into the live environment, i.e. choose the "try ubuntu" option on the installer medium, and set up my Linux partitions from there using Gparted, or at least the extended one. I believe it is possible to do all of this during the install, but I like to have them set up before I start the installer.

As Mark Phelps has already pointed out, you will need to choose the "something else" option at the point where the installer wants to know if you want to "use the whole drive" or "install beside windows". This will put you in the manual partitioning mode, and allow you to choose to install to the space or partitions you have prepared.

You asked about mount points. That is fairly simple. If you picture your file system as a tree, the mount point is the point in the structure where a directory is stuck to the tree. When you do your install, you need to know at least that the partition where the system installed to is to be mounted at / . That is the base (or tip...) of the whole file system. Everything else is mounted "inside" that. When you seed a path like /home/username/pictures/great_photo.jpg it means "the jpg file *great_photo* which is in the directory *pictures* which is in the directory *username* which is in the directory *home* which is in the file system" .

The other mount point you will definitely see during your install is /swap. You should create a swap partition. If you want the hibernate function to work, this should be a little bigger than your RAM. If the hibernate function (which  writes the contents of RAM to the swap space for retrieval when you wake up the computer) is not important, you wont really need much more than a GB or so of swap. Even that is generous for a machine with a modern amount of RAM, but you shouldn't have to worry about 1GB of drive space on a modern machine.

You might want to think about making a separate partition for your /home. The /home/username directory is where the system puts your user config files, and where your data is stored by default. If this is on a separate partition, it can be re-mounted should you need to re-install. You don't need to do this, but I have found it helpful a number of times in the past.

The partition that the system goes on (which is mounted at / ) should have at least 10 - 15GB. If you do not have a separate /home partition, it should be more, because then /home will be in there as well, and you will need space for your files. If you decide to make /home separate, do about 10 - 15GB for /, and the rest of your available space for /home (with a GB for /swap in both cases).

---

### Post by oldfred on 2013-02-22
Windows may not show more than c: & d:. The 100MB boot partition is hidden and often the vendor tools or vendor recovery is hidden. Only from the partition tools will you see the extra partitions.

From liveCd you can post this to see actual partitions.

sudo fdisk -lu 
or
       sudo parted /dev/sda unit s print
    
With MBR(msdos) partitioning you can only have 4 primary partitions, but you can make one primary the extended partition which is just a container for many logical partitions. Windows needs a primary to boot from, but Linux boots from logical just fine.

---

### Post by whyaname on 2013-02-22
I allocated 50 gb from my D drive and while installing Ubuntu, I chose the install Ubuntu alongside Windows 7 option. Does that make a difference?

---

### Post by whyaname on 2013-02-22
I have a dual boot system and it went without any major hassles. Thanks for all your help.

---

