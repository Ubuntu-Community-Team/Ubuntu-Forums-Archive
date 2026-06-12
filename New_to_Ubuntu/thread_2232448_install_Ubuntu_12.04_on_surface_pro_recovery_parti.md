---
title: "install Ubuntu 12.04 on surface pro recovery partition"
date: 2014-07-02
forum: New to Ubuntu
---

### Post by Leon_Overweel on 2014-07-02
Hey 

So I need to install Ubuntu 12.04 (newer versions aren't supported by the software I need to use yet) on my surface pro. Since the C drive is nearly full, I decided to remove the ~7 GB Windows recovery thing and put it on a USB disk. I used this guide for that: [http://www.microsoft.com/surface/en-us/support/storage-files-and-folders/create-a-recovery-drive](http://www.microsoft.com/surface/en-us/support/storage-files-and-folders/create-a-recovery-drive) 

That caused a chunk of ~7.8 GB of space to be freed up on my hard drive, but because of the way it was positioned (there's some other ~300 MB recovery thing between the C drive partition and the newly freed up space, and moving utilities wrong let me reorder them), I can't extend the C drive to add that space, and my only option was to mount it as a new drive (called my D drive).

So how do I install Ubuntu on that 7.8 GB partition if I have a bootable SD card with Ubuntu 12.04 on it?

Some other things:
- I have a bootable SD card with Ubuntu 12.04 on it, but the ISO I had to use to make that has the word AMD in it, which seems odd considering there's an i5 in my surface (I can only get the AMD ones to boot for all the versions of Ubuntu I've tried (12, 13 and 14); the ones that say i and then some numbers which on the downloads page say they're for most Windows computers aren't recognized when I try to boot to them and it just goes straight to Windows)
- I've previously tried just running it from the SD card, but that won't allow me to give Ubuntu more than 4 GB of source which isn't enough to install all the software I need
- When I run the install from the SD card, the installer says it doesn't recognize any operating systems (despite the fact that I have Windows 8.1 Update installed), and I only get the options to erase my hard drive (which I can't do because I need Windows too) and to do the custom install (and there I don't know what to pick to install it to that D drive because all I see are things that start with sda), but not the option that's in most installation guides that says "install Ubuntu alongside [operating system]

Any help is much appreciated because I can't start the actual work I'm supposed to be doing at this internship without having it working, and I've wasted the past two days trying to get it to install.

Thanks

---

### Post by Mark Phelps on 2014-07-02
Drive letters are only used in MS Windows; thus, you can't install Ubuntu to the "D:" drive; instead, you need to remove that "drive" (actually, it's a partition), and then use the Something Else option in the Ubuntu installer to format that empty space.  Ubuntu can't be installed to a Windows filesystem partition.

---

### Post by buzzingrobot on 2014-07-02
7 gigs is a rather tight fit for Ubuntu. I'd guess the actual OS will fit, but then there's the issue of a swap partition and space for files and applications added later.

The "AMD" in the iso image file name is a reference to the 64-bit architecture the image targets, not a reference to the corporation. Images "that say i and then some numbers" are intended for 32-bit systems. The reference to "most Windows computers" is intended to mean that 32-bit images will work on both 32-bit and 64-bit machines.  I.e., Windows computers are, by definition, either 32-bit or 64-bit, and many users probably don't know which they have. 

If the image is bootable, and if you've told the BIOS to boot off the USB card, and the image is correctly burned to the card, it will boot. It may be that 32-bit images won't boot on the Surface, so the BIOS moves on to the next option.

I believe deleting the Windows recovery partition means Windows can be re-installed only by booting a standard install DVD?

---

