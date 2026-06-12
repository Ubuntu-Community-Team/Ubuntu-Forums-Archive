---
title: "32bit vs 64bit"
date: 2012-02-14
forum: Recurring Discussions
---

### Post by spillage2 on 2012-02-14
Hi all,

I hope I dont sound too stupid..I know the main differences between these two os versions but am just wondering if both would use the same /home.

can you install both type on one system and have them share the same /home.

I know windoz 64 bit is a bit of a waste of time from what I have heard but assume the a linux version would be very usable?

Cheers.

Spill.

---

### Post by oldfred on 2012-02-14
Moved to reoccurring discussions.

You should not share /home with two systems unless you use different user names so you do not have the same user settings. Programs are designed for upgrades so the reuse of a /home on a new install of a newer versions works, but different settings in different systems may create conflicts.

There is no reason not to run the 64 bit version. In 12.04 Ubuntu will finally suggest it as the preferred choice. But it should have been use by anyone with 64bit hardware for the last couple years.

---

### Post by kurt18947 on 2012-02-14
I've been using 64 bit on 64 bit capable systems for a while.  One thing to be aware of is drivers and your existing hardware.  For instance, I have a Brother printer which does not have built-in support.  I must user drivers from Brother which are available and work well.  However they're 32 bit only.  Brother does provide instructions and support for installing on 64 bit systems, it just needs to be done via the command line.  Another example is softmaker office 8.  It is offered for free but AFAIK it's available in 32 bit only.  Newer versions are available in 64 bit.  I've tried a little bit to install on a 64 bit system.  It will install but won't start.  Just something to consider when installing 64 bit.

---

### Post by wolfen69 on 2012-02-14
> **kurt18947 said:**
> I've been using 64 bit on 64 bit capable systems for a while.  One thing to be aware of is drivers and your existing hardware.  For instance, I have a Brother printer which does not have built-in support.  I must user drivers from Brother which are available and work well.  However they're 32 bit only.  Brother does provide instructions and support for installing on 64 bit systems, it just needs to be done via the command line.  Another example is softmaker office 8.  It is offered for free but AFAIK it's available in 32 bit only.  Newer versions are available in 64 bit.  I've tried a little bit to install on a 64 bit system.  It will install but won't start.  Just something to consider when installing 64 bit.

You can force 32bit drivers to work in 64, so it's no big deal. 99.99% of all hardware will work (as compared to 32bit) without issue. I myself have never had any problems in over 2 years of using 64bit on various computers. There's a reason why ubuntu is making 64bit the default, and it's about time.

---

### Post by Shibblet on 2012-02-14
> **spillage2 said:**
> I know windoz 64 bit is a bit of a waste of time from what I have heard but assume the a linux version would be very usable?

Cheers.

Spill.

Correct me if I am wrong, but I understood it like this...

With Windows and Linux, I believe the benefit of running a 64bit system is memory access.  If you have 4 Gigs of RAM or more, you need 64bit memory access in order to utilize all of your memory.

The only problem with Windows is that a majority of the programs are still only 32 bit.  Including most games.  In Linux (Ubuntu) if you install a 64bit OS, most of the packages are recompiled for 64 bit and will run in your larger memory area.

So, if you download Firefox for Windows 7, you will only get the 32 bit version, and it will only run in your first 4 gigs of RAM.  In Ubuntu, it is has been compiled in 64 bit, and will utilize more of your available RAM if necessary.

---

### Post by wolfen69 on 2012-02-14
> **Shibblet said:**
> Correct me if I am wrong, but I understood it like this...

With Windows and Linux, I believe the benefit of running a 64bit system is memory access.  If you have 4 Gigs of RAM or more, you need 64bit memory access in order to utilize all of your memory.

The only problem with Windows is that a majority of the programs are still only 32 bit.  Including most games.  In Linux (Ubuntu) if you install a 64bit OS, most of the packages are recompiled for 64 bit and will run in your larger memory area.

So, if you download Firefox for Windows 7, you will only get the 32 bit version, and it will only run in your first 4 gigs of RAM.  In Ubuntu, it is has been compiled in 64 bit, and will utilize more of your available RAM if necessary.
Plus, on windows, things have to be "certified" to be able to use them on 64bit windows. Last time I checked, that was the case.

---

