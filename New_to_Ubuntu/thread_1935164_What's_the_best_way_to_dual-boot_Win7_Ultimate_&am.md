---
title: "What's the best way to dual-boot Win7 Ultimate &amp; Lucid Lynx"
date: 2012-03-03
forum: New to Ubuntu
---

### Post by S2UIRR3L on 2012-03-03
I've dual-booted computers before, but they started out with XP and Jaunty Jackalope.
Will it be the same if I dual-boot a Win7 with Lucid (will I get to choose OS at startup)?

I'm pretty much a newbie (and learning, BIG thanks to everyone here on the forums)
and every time I installed Ubuntu, there was a GRUB thing automatically installed, so?

Big thanks in advance!
-Leo in Massachusetts

---

### Post by Frogs Hair on 2012-03-03
Yes , you will have a choice at boot .Start by looking at documentation and there are a number text and video tutorials easily found with a search.   

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by nd456 on 2012-03-03
Just to let you know... Grub looks different than it did that long ago... I would recommended allocating Ubuntu the maximum hard drive space possible.

---

### Post by S2UIRR3L on 2012-03-03
As long as I can install Lucid Lynx on a second partition and have "some" sort of "thing" that resembles (or at least works like) grub, and installs it's self automatically, that's all I need.

And now that I have "this" much information, I can start loading OS's onto my new hard drive... I'm guessing load Win7 first, THEN install Lucid second ('cause Win7 wants everything).

I'll mark this thread as SOLVED in a few days from now. I'll leave it open for now so other people can comment if they know anything else that I should know and/or consider.

Thanks all!!!

EDIT: I'm splitting the hard drive right down the middle. 40-Gigs for Win7 / 40-Gigs for Lucid (I use external 500-Gig for storage)

---

### Post by pootan on 2012-03-03
Yes Windows install first then Lucid. The Ubuntu bootloader is much more friendly than Windows.

---

### Post by presence1960 on 2012-03-03
> **pootan said:**
> Yes Windows install first then Lucid. The Ubuntu bootloader is much more friendly than Windows.

**_If you are noobish install windows first, then Ubuntu._** 

You are right where you need to be now. When you become more skilled at Linux and partitioning you will find that you don't need to install windows first nor on the first primary partition. Windows can be installed to any primary partition. I have Windows 7 on sda4.

If you need help check back in.

P.S. Was just reaffirming pootan's suggestion, post not directed at pootan but rather at OP

---

### Post by Mark Phelps on 2012-03-04
Once you have Win7 installed, if you want to be sure that nothing happens to it, then follow the suggestions below:

Use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space. When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

