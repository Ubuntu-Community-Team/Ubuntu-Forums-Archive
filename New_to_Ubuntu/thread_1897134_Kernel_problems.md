---
title: "Kernel problems"
date: 2011-12-18
forum: New to Ubuntu
---

### Post by TREESofRIGHTEOUSNESS on 2011-12-18
I ran a post a while back about acpi=off param needed to boot.
I have circumvented the problem thanks to Toz and the incredible help given, and now have a working 11.10 with the lucid Kernel.
I have posted a bug in launchpad, and questions on askubuntu, and other things.
So... I am attempting once again to figure out what the bug is.  The kernel broke in the transition to Maverick.  I saw on the release notes that CMOV support and older processors are no longer supported.... but someone pointed out to me that my computer has neither issue. 
Basically I need to find out WHO to contact, or WHAT to look for.  I have plenty of my info listed here
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/903961](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/903961)

I have been dealing with this for over a year (obvious from, Maverick)
So I am dualbooting my stable Lucid, and my experimental Oneric with Lucid kernel.
So far Oneric w lucid kernel works great, but I know it is not recommended and could cause some problems, which is why I use Lucid normally, and only have oneric to test, and post info, and try patches (if any exist)

Any help is very appreciated.

---

### Post by sudodus on 2011-12-18
I see that you have a Hewlett-Packard Presario R3200 (PF153UA#ABA)

Have you tried several of the suggested boot options? Not only acpi=off, but the others:
noapic nolapic nomodeset ...

---

### Post by TREESofRIGHTEOUSNESS on 2011-12-18
yes....and the only other one that work (well... some of the time) was the acpi_osi=/"Windows 2001 SP1/" (or 2006, or 2001 SP2 but none worked all the time)  acpi=off was the only one that works consistantly.  Sometimes booting recovery mode and then selecting "resume normal boot" works... but not always.  acpi=off doesn't work in the 64bit either... and it would sometimes boot normally.
I have tried just about everything I can try, now I need to find out where to go to get the problem resolved

---

### Post by sudodus on 2011-12-18
It is strange that some options work ***sometimes***. Could it be that something is not quite 'awake' when it is needed? What if you wait for ten extra seconds at the grub menu? (You can test it manually stopping the countdown with the up/down arrow keys, and make it permanent later in the grub configuration.)

---

### Post by TREESofRIGHTEOUSNESS on 2011-12-18
no... it hangs up during the boot, after I have put in options... it is after the floppy and firewire load.
Grub does fine.... I have set it to an indefinite wait before, and there was no change

---

### Post by sudodus on 2011-12-19
I have no more ideas now. Let us hope someone else ...

---

### Post by bodhi.zazen on 2011-12-19
The thing is, kernels move on.

So, in your bug report, you were asked to test the latest kernel, did you do that ?

Either the problem will persist (most likely) in which case they well investigate, or it will be resolved.

But they are not going to fix a previous kernel release.

So you need to test with a mainline kernel

[https://wiki.ubuntu.com/Kernel/MainlineBuilds?action=show&redirect=KernelMainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds?action=show&redirect=KernelMainlineBuilds)

---

### Post by TREESofRIGHTEOUSNESS on 2011-12-19
Yeah I tried 3.2-rc2-oneric 3.2-rc4-oneric (as I am testing oneric on m other partition)
I even  updated the tag to include "kernel-bug-exists-upstream"
I will continue to test things.  So far running the last Lucid kernel allows the system to run without any noticeable flaws... though there may be some I am unaware of.

surely there is some way to add a patch or a module or something?

What more can I post, and look for?

---

### Post by bodhi.zazen on 2011-12-19
> **TREESofRIGHTEOUSNESS said:**
> Yeah I tried 3.2-rc2-oneric 3.2-rc4-oneric (as I am testing oneric on m other partition)
I even  updated the tag to include "kernel-bug-exists-upstream"
I will continue to test things.  So far running the last Lucid kernel allows the system to run without any noticeable flaws... though there may be some I am unaware of.

surely there is some way to add a patch or a module or something?

What more can I post, and look for?

If you tried the mainline kernel, you need to then update your bug report and the kernel team will start to look at the problem.

---

### Post by TREESofRIGHTEOUSNESS on 2011-12-19
> **bodhi.zazen said:**
> If you tried the mainline kernel, you need to then update your bug report and the kernel team will start to look at the problem.

What do you mean update it?
I updated the tags (as I was told to do when I tested it).  Do I need to install the kernels again and run ubuntu-bug linux again?

---

### Post by bodhi.zazen on 2011-12-19
> **TREESofRIGHTEOUSNESS said:**
> What do you mean update it?
I updated the tags (as I was told to do when I tested it).  Do I need to install the kernels again and run ubuntu-bug linux again?

Looking at the bug report now, looks as if you are good to go.

---

### Post by TREESofRIGHTEOUSNESS on 2012-10-18
I'd like to close this thread as it is being fixed.  Mr. Salisbury is performing a Kernel bisection.  All further information will be posted in the bug's webpage.
[https://bugs.launchpad.net/bugs/903961](https://bugs.launchpad.net/bugs/903961)

---

### Post by TREESofRIGHTEOUSNESS on 2013-03-21
The bug was fixed in the AMD64 branch of the OS starting with 12.04.  Everything works as it should now.

---

