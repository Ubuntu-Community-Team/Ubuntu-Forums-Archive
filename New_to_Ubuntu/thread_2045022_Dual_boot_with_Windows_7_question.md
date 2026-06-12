---
title: "Dual boot with Windows 7 question"
date: 2012-08-20
forum: New to Ubuntu
---

### Post by Sly14Cat on 2012-08-20
Hello,
I want to install Ubuntu along Windows 7 and I was told not to choose dual boot because of the fragmentation of Windows. My computer is fairly new and doesn't have many files. If I were to defragment the computer and give ubuntu 5gb of space using the dual boot option, could I extend the Ubuntu partition later?

(Windows says I can shrink the drive down to 436.5gb out of 911gb.)

---

### Post by SeijiSensei on 2012-08-20
With a drive as large as yours, why not give Ubuntu some space to operate, say 40-50 GB?

---

### Post by kurtymckurt on 2012-08-20
I've dual booted for a while now. I have ubuntu 12.04 and windows 7.  I haven't had any problems going back and forth or with windows fragmentation. 

My advice would be to do proper backups of personal information and if you don't like the setup, just wipe it all with a clean install with the OS of your choice.

---

### Post by benhanby on 2012-08-20
There is a program called g-parted yo can use it to put and change partitions on other devices so i imagine you could use it for your own computer! check through the program first though . Make sure you know fully how to use it before you do !

---

### Post by Mark Phelps on 2012-08-20
DO NOT, repeat NOT, use GParted to shrink down your Win7 install to make room for Ubuntu.  Doing so risks corrupting the Win7 filesystem, and if that happens, Win7 will then be unbootable.

If you really want to dual-boot with Win7, then continue reading ...

You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by lwalper on 2012-10-02
Ditto Mark Phillips: use the Win7 utilities for Windoze adjustments. Though gparted will probably do the job you probably ought to stick with the M$ version for adjusting the Windoze environment. I have just installed a dual-boot Vista / Ubuntu on a drive with 320Gb HDD creating a 50Gb primary partition for Vista, 50Gb primary partition for Ubuntu and the balance in an extended partition for common Vista / Ubuntu files formatted in FAT32 so both OSs can read the partition. Depending on which OS I'm booted into I can use Excel or LibreCalc, WordPerfect or LibreWrite.

I don't know if the Windoze defragmenter does a disk check operation, but in the past, before defragmenting I've always gone to the prompt and run chkdsk c:\ /f which fixes errors on the volume, then run the defragmenter.

---

### Post by Wim Sturkenboom on 2012-10-02
It was already mentioned but do yourself a favor and give it enough space. 50GB should be enough to allow you to download updates, install other software etc etc. while you get your feet wet.

You will regret it if you only give it 5GB.

---

### Post by cthom on 2012-10-02
or use wubi :)

---

### Post by Bufeu on 2012-10-02
> **cthom said:**
> or use wubi :)
Wubi shouldn't be used for long-time installs.

---

### Post by Mark Phelps on 2012-10-03
> **cthom said:**
> or use wubi :)

The problem with using Wubi is when you later want to MOVE it to its own partition.  IF you start with the 4-partition limit and use Wubi to bypass that, when then want to move it -- you're back to square 1 -- but even worse!

Why?

Because now, you've installed Ubuntu INSIDE one of your partitions, so shrinking it to create room for Ubuntu may simply be not possible.

If you have 4 partitions, you can't simply create a fifth to hold the migrated Wubi setup because that resurfaces the original "Dynamic Disk" problem.

So basically, unless you really are only interested in a short-term experiment, you need to consider the more permanent separate partition solution up front.

---

