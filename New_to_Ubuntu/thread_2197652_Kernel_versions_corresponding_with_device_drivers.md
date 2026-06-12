---
title: "Kernel versions corresponding with device drivers"
date: 2014-01-04
forum: New to Ubuntu
---

### Post by BostonLinux99 on 2014-01-04
Dear Community,

I'm new to Linux but a web applications developer on other platforms for a number of years and trying to learn Linux.
I have recently set up a bunch of Lubuntu, Xubuntu, Ubuntu installation - 12.04 & 13.10 - and worked through a lot of issues over a few days with versioning and drivers.  Everything is working now, but had a few concepts to learn.

My question is - Linux Kernel version, and it's relationship with Ubuntu device drivers?
What is the basic gist of compatibility of proprietary drivers or any drivers and linux kernel version?

I hear folks talk about recompiling things... I don't know how to do that.
But it seems developer communities or companies release updates periodically corresponding with Kernel updates.

Any info for this noob would be helpful.
I have been reading online, but sometimes formum answers are great for others so hoping someone has a few secs to type a couple sentences if they get it well.

Thank you.

---

### Post by sandyd on 2014-01-04
> **jaytorian said:**
> Dear Community,

I'm new to Linux but a web applications developer on other platforms for a number of years and trying to learn Linux.
I have recently set up a bunch of Lubuntu, Xubuntu, Ubuntu installation - 12.04 & 13.10 - and worked through a lot of issues over a few days with versioning and drivers.  Everything is working now, but had a few concepts to learn.

My question is - Linux Kernel version, and it's relationship with Ubuntu device drivers?
What is the basic gist of compatibility of proprietary drivers or any drivers and linux kernel version?

I hear folks talk about recompiling things... I don't know how to do that.
But it seems developer communities or companies release updates periodically corresponding with Kernel updates.

Any info for this noob would be helpful.
I have been reading online, but sometimes formum answers are great for others so hoping someone has a few secs to type a couple sentences if they get it well.

Thank you.
Drivers in Ubuntu are loaded as kernel modules (except for the ones that are compiled into the kernel). Kernel modules may come with the kernel, or can be installed externally (i.e. Nvidia graphics drivers, ATI graphics drivers, Broadcom STA)

---

### Post by QIII on 2014-01-04
Hello!

Unless you are planning to alter source code for some specific reason, there is very little reason to compile almost anything these days.  I sometimes chuckle when I see instructions that call for compilation/building -- they are often less practical than they are "impress your geek friends" in nature.

As for driver/kernel compatibility, the steps are usually small seesaws that don't interfere with each other and cause problems.  Keep kernels and drivers updated and you usually don't run into problems.  Still, there are times when an OEM changes a driver and the newest is incompatible with a particular kernel or vice versa.  We do deal with that problem occasionally in the Linux world.  Microsoft has the market share gravity to hold OEMs in orbit.  Linux doesn't.

Problems are rare, but they do happen and occasionally they are quite problematic.  But the community usually moves very quickly to find solutions on the Linux end.  We can't do much at all about the OEM end when drivers are proprietary.

Bottom line:  I generally wouldn't fret much.  It has been a very long time, years perhaps, since I have encountered anything catastrophic.

---

### Post by BostonLinux99 on 2014-01-05
Thank you.  I will do that.

---

