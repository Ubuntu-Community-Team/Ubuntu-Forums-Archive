---
title: "Ubuntu Windows Installer"
date: 2012-09-18
forum: New to Ubuntu
---

### Post by joeqesi on 2012-09-18
Hi guys, I've just bought a new laptop that has Windows 7 pre-installed on it and I want to switch from Windows 7 to Ubuntu.

I was going to use the Windows Installer for Ubuntu but I was wondering what would happen to Windows 7, would it still be on the laptop? If so, how do I uninstall it?

---

### Post by newb85 on 2012-09-18
> **joeqesi said:**
> Hi guys, I've just bought a new laptop that has Windows 7 pre-installed on it and I want to switch from Windows 7 to Ubuntu.

I was going to use the Windows Installer for Ubuntu but I was wondering what would happen to Windows 7, would it still be on the laptop? If so, how do I uninstall it?

If you just bought a new laptop, I would assume that it has plenty of HD space for both Windows and Ubuntu.  If you run the machine dual-boot, then the only resource expense of keeping Windows around is your HD space.

If you plan to eliminate Windows now or down the road, you should *not* use the Windows installer for Ubuntu.  Instead, download the .iso for Ubuntu, burn it to a CD and boot from the CD.  That installer is extremely easy to use.

Edit: to boot from the CD, have the CD inserted when you turn the machine on, and hold down Shift when the screen with the manufacturer's logo pops up.  That should bring up the boot options.

---

### Post by joeqesi on 2012-09-18
Would Windows still be on the hard drive once I installed it from the cd? Or would I still have to figure out how to remove it?

---

### Post by newb85 on 2012-09-18
> **joeqesi said:**
> Would Windows still be on the hard drive once I installed it from the cd? Or would I still have to figure out how to remove it?

The installer on the CD will give you the options to install alongside or in place of Windows.

---

### Post by Mark Phelps on 2012-09-18
IF you're seriously considering dual-booting, do NOT just blindly stick in the disk and drag the slider.  That is asking for trouble.  Instead, read through the material below ...

You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by JKyleOKC on 2012-09-18
> **Mark Phelps said:**
> Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.This is true for "MBR Legacy" systems, but many if not most systems sold since 2011 use the newer "UEFI" boot technique and "gpt" partitioning, which has no four-primary limit and which is totally incompatible with much existing knowledge. A wiki page that spells out the differences in quite simple terms is at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) and is recommended reading for anyone installing any of the *buntu family on a recent system. Doing so can prevent serious amounts of panic (BT, DT)...

---

### Post by joeqesi on 2012-09-18
Fair enough, thanks for the help guys.

---

### Post by newb85 on 2012-09-18
> **JKyleOKC said:**
> This is true for "MBR Legacy" systems, but many if not most systems sold since 2011 use the newer "UEFI" boot technique and "gpt" partitioning, which has no four-primary limit and which is totally incompatible with much existing knowledge. A wiki page that spells out the differences in quite simple terms is at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) and is recommended reading for anyone installing any of the *buntu family on a recent system. Doing so can prevent serious amounts of panic (BT, DT)...

So, does the installer handle a UEFI system properly by default?

---

### Post by JKyleOKC on 2012-09-18
In my experience, no it does not. It installed 12.04.1 as MBR Legacy on a Win7 system that was UEFI, never even mentioning that a problem could exist. That was my "been there, done that" experience and is what sensitized me to the situation.

The bug in the installer has been reported and is being addressed. Meanwhile the UEFI link I posted tells how to do it properly and force the system to behave.

---

### Post by newb85 on 2012-09-18
@JKyleOKC,

Thanks, I'll keep that in mind.

---

