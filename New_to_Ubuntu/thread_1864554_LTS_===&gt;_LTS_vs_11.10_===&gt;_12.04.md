---
title: "LTS ===&gt; LTS vs 11.10 ===&gt; 12.04"
date: 2011-10-19
forum: New to Ubuntu
---

### Post by fleamour on 2011-10-19
How do the kernel versions marry up between LTS to LTS upgrade as opposed to 11.10 (normal release) to 12.04 (LTS) upgrade?

I ask because 10.04 LTS is only on kernel 2.6.32-34, it does not even support TRIM yet.  This is a good thing because updates filter down resulting in a more stable platform.  My C2D tower, running a normal release, has been thrown the odd curve ball with a rouge update upsetting the apple cart.  My ancient laptop running LTS has been stable as a table.  No such problem.

So will the 12.04 LTS kernel suddenly be bumped to match the current normal release?  (Way ahead by all accounts) I cannot get my head around how it will work in practise & have not been around long enough to know.

---

### Post by mcduck on 2011-10-19
12.04, when released, will be the current normal release. There are no separate normal and LTS versions released at the same time.

So 12.04 will have a newer kernel version than any version released before it. Exactly like any other Ubuntu release version does, it will use the latest stable Linux kernel version available at the moment.

---

### Post by Paqman on 2011-10-19
12.04 will have a brand new kernel, exactly which one isn't decided yet, but TRIM has been supported for a while now so you can bank on that.

Generally speaking the LTS release is handled pretty much the same way as a 6-monthly release. So expect update packages, an updated kernel, etc. They may delay some of the more radical changes for 12.10, so the actual changes compared to 11.10 will probably be quite conservative. But compared to 10.04 it'll be a quantum leap.

---

### Post by fleamour on 2011-10-19
Thanks for explaining!

I have high hopes, 11.04 had me excited with the new XFCE auto-hide/show bottom panel.  Shame the wireless did not work for me.  10.10 would not even load, have not tried 11.10.  If everything plays nice, no glaring bugs, I'll stick with 12.04 LTS.  Seems a lot less hassle in the long run.

---

### Post by kaldor on 2011-10-19
Check out the Linux Kernel release cycle. Every 6 months Ubuntu uses the latest stable kernel at that time. As of writing this, that would be 3.0.6. There's a release candidate for 3.1 right now which should be out soon.

An LTS release will likely keep the stable kernel release at that time, but backport extra features from subsequent kernel releases (hardware support). I'm not 100% sure on how Ubuntu does this, but I think I have the correct idea.

---

### Post by ExpertNovice on 2011-10-19
At least from the desktop perspective, cruising the development section of synaptic package manager for 10.04 LTS, kernels for 10.10 and 11.04 are present (search on maverick or natty). Although the kernel source had to be obtained by downloading from the release itself, headers are present for install purposes. My need was for DVB-T tuner operation, but the principle is the same. Older hardware may have issues wth correct function e.g. my old vintage laptop couldn't use 2.6.38.12 (which has TRIM?) because the old 173 nvidia driver will not build properly using DKMS. This is a known issue at 11.04 too. The point is it gives you time to do these things without a total upgrade at the vendor's schedule.

---

### Post by 3rdalbum on 2011-10-19
If you want, you could install a newer kernel for your 10.04 LTS. Either use a PPA or manually compile the latest kernel with Ubuntu patches - there should be a post on the Ubuntu wiki about how to do this.

If the new kernel doesn't work out, then just remove it and GRUB should update itself.

---

### Post by rbellah on 2011-10-19
I too am running 10.04for one reason, 11.04 and 11.10 run fine on the cd trial, no prob;ems, but load them on the HD and try to run it and wham no Ubuntu after the purple boot screen.  Very dissatisfied that these problems were not addressed by the developers on 11.10, stop making work a-rounds and get the basic system where it works for all as did on the releases up to 10.04

---

### Post by mcduck on 2011-10-19
> **rbellah said:**
> I too am running 10.04for one reason, 11.04 and 11.10 run fine on the cd trial, no prob;ems, but load them on the HD and try to run it and wham no Ubuntu after the purple boot screen.  Very dissatisfied that these problems were not addressed by the developers on 11.10, stop making work a-rounds and get the basic system where it works for all as did on the releases up to 10.04

Did you file a bug report? If not, the developers are much less likely to find out about the problem and come up with a fix for it...

Anyway, your problem has more likely something to do with your video drivers than the actual Ubuntu system, especially if you are using a graphics card that requires proprietary drivers.

---

### Post by snowpine on 2011-10-19
If you are a visual thinker, you might find this chart helpful:

[http://distrowatch.com/ubuntu](http://distrowatch.com/ubuntu)

---

