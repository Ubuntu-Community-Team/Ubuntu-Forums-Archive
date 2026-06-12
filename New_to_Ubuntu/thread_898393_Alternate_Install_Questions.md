---
title: "Alternate Install Questions"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by TJCIB on 2008-08-23
I have an old Compaq Prosignia 150 laptop with these specs:
AMD K6 
64-MB SDRAM
6-GB HDD
4X DVD-ROM

A few issues I am trying to resolve:
There are no networking capabilities, it has a pcmcia slot, but no card.  So to update I plan on downloading the packages on my other ubuntu system, then transferring them over via pen drive and running dpkg

I do have a USB Wireless adaptor, but this will be my first try to get wireless working.  Should the normal how tos work the same on an alternate install as with a regular?

Finally, can anyone recommend a good, lightweight PowerPoint viewer.  This system will mostly be used for my students doing their presentations.

If there are any other pitfalls I am overlooking, please let me know.

---

### Post by Flyingjester on 2008-08-23
with those specs, i would not recommend running ubuntu.. i would recommend DSL, or puppy linux.

---

### Post by TJCIB on 2008-08-23
Yea, I tried DSL on that system, I didn't like it for some reason.  I can't put my finger on why.

I'll take a look at Puppy Linux too before making any final decisions.

I was hoping to keep an Ubuntu base just because my students are familiar with it, since we use the full versions in our computer lab.  Yeah, it would look different, but kids love familiarity...

---

### Post by philinux on 2008-08-23
Even Xubuntu wont run.

> Minimum system requirements

To run the Desktop CD (LiveCD + Install CD), you need 128 MB RAM to run or 192 MB RAM to install. The Alternate Install CD only requires you to have 64 MB RAM.

To install Xubuntu, you need 1.5 GB of free space on your hard disk.

Once installed, Xubuntu can run with 192 MB RAM, but it is strongly recommended to have at least 256 MB RAM.

You'd be better with fluxbuntu unless you can get more ram.

---

### Post by Flyingjester on 2008-08-23
> **TJCIB said:**
> Yea, I tried DSL on that system, I didn't like it for some reason.  I can't put my finger on why.

I'll take a look at Puppy Linux too before making any final decisions.

I was hoping to keep an Ubuntu base just because my students are familiar with it, since we use the full versions in our computer lab.  Yeah, it would look different, but kids love familiarity...

trust me, i can totally understand that, but unfortunately with those specs, it would be difficult if not impossible to get ubuntu running.

---

### Post by snowpine on 2008-08-23
Hi TJCIB, I would not recommend any flavor of Ubuntu on that machine. Even the minimal install (10mb iso, command line only) will fail until this bug is resolved: [https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/202959](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/202959)

If you can find a workaround for that, you will either have to deal with a command-line system or install a lightweight windows manager like Openbox, IceWM, etc. You don't have anything near the resources for Ubuntu's Gnome desktop (256mb required, 512mb recommended). Forget about Powerpoint!

Why not try something designed for old computers (DSL, Puppy, Slitaz) rather than frustrate yourself trying to squeeze Ubuntu in there? :)

---

### Post by Bucky Ball on 2008-08-23
You are fighting an uphill battle with those specs. Or as we say here, trying to push s**t uphill with a pointy stick! DSL would be about it.

---

### Post by TJCIB on 2008-08-23
Yes, 
Unfortunately Windows 98 runs fine on it, including PowerPoint 2002.

The main problem is that pen drives don't automatically work on 98.  Its just a huge hassle.

Thanks for the [candid] advice...

---

