---
title: "kernel question"
date: 2007-10-27
forum: Programming Talk
---

### Post by go_beep_yourself on 2007-10-27
Will a vanilla kernel without any special patches not compile on Ubuntu? I'd like to use a newer kernel than the one from the linux-source package.

---

### Post by kast on 2007-10-27
You can compile a vanilla Kernel on Ubuntu, its just up to you to make sure your compiling it with the right stuff you need.

---

### Post by go_beep_yourself on 2007-10-27
> **kast said:**
> You can compile a vanilla Kernel on Ubuntu, its just up to you to make sure your compiling it with the right stuff you need.

Can you give me some examples of stuff I might need that a vanilla kernel does not include?

---

### Post by kast on 2007-10-27
Linus Torvalds keeps releasing new versions of the Linux kernel. These are called "vanilla" kernels, meaning they have not been further modified by anyone. Many Linux operating system vendors modify the kernels of their product, mainly in order to add support for drivers or features which have not officially been released as stable, while some distributions rely on vanilla kernels.

Source 
[http://en.wikipedia.org/wiki/Linux_kernel](http://en.wikipedia.org/wiki/Linux_kernel)

So basic you want to make sure you add support in your kernel for your hardware etc..

---

### Post by go_beep_yourself on 2007-10-27
> **kast said:**
> Linus Torvalds keeps releasing new versions of the Linux kernel. These are called "vanilla" kernels, meaning they have not been further modified by anyone. Many Linux operating system vendors modify the kernels of their product, mainly in order to add support for drivers or features which have not officially been released as stable, while some distributions rely on vanilla kernels.

Source 
[http://en.wikipedia.org/wiki/Linux_kernel](http://en.wikipedia.org/wiki/Linux_kernel)

So basic you want to make sure you add support in your kernel for your hardware etc..

I see. I'm not sure if all of my hardware is or is not supported by the vanilla kernel. Do you use the linux-source ubuntu package?

---

### Post by kast on 2007-10-27
go_beep_yourself so the Vanilla Kernel has what the previous Kernels have, but there not pre built for an specific distribution of Linux. so its up to you to make sure your selecting the right modules etc.. in the kernel for your hardware, or for what you will be using it for, before you build.

The vanilla Kernels are better for the reason that you know that there not going to be a bunch of stuff in there that you might not need. there also dangerous if you don't know what your doing you could end up with allot of your system just not working.

Always backup your previous kernel before you move in the new.

I use the one that comes with Ubuntu, but i compile  my own when i was running slackware

---

### Post by go_beep_yourself on 2007-10-30
> **kast said:**
> go_beep_yourself so the Vanilla Kernel has what the previous Kernels have, but there not pre built for an specific distribution of Linux. so its up to you to make sure your selecting the right modules etc.. in the kernel for your hardware, or for what you will be using it for, before you build.


What's modules are available from the linux-source package that aren't available with a vanilla kernel from kernel.org?

---

### Post by winch on 2007-10-30
You could diff the ubuntu kernel source against the same version vanilla source to see what changes have been made. I guess it would take a fair bit of work to convert the diff into something meaningfull.

I've seen the question asked several times but have never seen a better answer than that. Most Distros appear just to make the source available not any information on patches they have applied to it.

You could compile the vanilla source using the ubuntu config and see if it works.

---

### Post by moma on 2007-10-30
For some time ago, I compiled a _vanilla_ kernel under Ubuntu.
Maybe you do not read "scandinavian" languages, but study the commands
[http://www.futuredesktop.org/kompilere_kjerne.html](http://www.futuredesktop.org/kompilere_kjerne.html)
( of course the kernel v2.6.19 is very old  )

It's important that you do not start from scratch but take a copy of a "config" file from an existing (good) kernel and run "make oldconfig" on it,  as you can see in step 5) 

# cd /usr/src/linux
# cp /boot/config-`uname --kernel-release`  ./.config
# make oldconfig
etc..

---

### Post by go_beep_yourself on 2007-10-30
> **winch said:**
> You could diff the ubuntu kernel source against the same version vanilla source to see what changes have been made. I guess it would take a fair bit of work to convert the diff into something meaningfull.

I've seen the question asked several times but have never seen a better answer than that. Most Distros appear just to make the source available not any information on patches they have applied to it.

You could compile the vanilla source using the ubuntu config and see if it works.


I have done that. The only thing I saw that did not work was VMware Server. The module for it would not compile either, and I had the linux source headers installed for the vanilla kernel, so now I am using the kernel that I compiled from the linux-source package (it is older than the ubuntu stock kernel).

---

### Post by go_beep_yourself on 2007-10-30
> **moma said:**
> For some time ago, I compiled a _vanilla_ kernel under Ubuntu.
Maybe you do not read "scandinavian" languages, but study the commands
[http://www.futuredesktop.org/kompilere_kjerne.html](http://www.futuredesktop.org/kompilere_kjerne.html)
( of course the kernel v2.6.19 is very old  )

It's important that you do not start from scratch but take a copy of a "config" file from an existing (good) kernel and run "make oldconfig" on it,  as you can see in step 5) 

# cd /usr/src/linux
# cp /boot/config-`uname --kernel-release`  ./.config
# make oldconfig
etc.

When I compiled a vanilla kernel, I did not have to use make oldconfig to use an existing config file. All I did was copy it from the /boot directory and renamed it to .config. I then made a few changes to that config of mostly getting rid of some things that were not needed for my system. I never had to use make oldconfig. What does that do, and why didn't I need it? I searched the make man page for oldconfig and did not find anything.

---

### Post by tehtrk on 2007-11-07
It's a shame if isn't any documentation that describes what patches the ubuntu devs apply to the vanilla kernel. 

Winch don't take this personally I but disagree with the philosophy that most distros don't do X so why should we. 

I'm just glad I didn't have to hear "why would you want to compile your own kernel?". The freedom of choice that linux offers should apply to all distros, especially those that call themselves "free" (as in freedom). I recall someone on launchpad talking about controlling cpufreq governors through an applet, and one person replied with "And why should a normal user be able to change the CPU speed in the first place? The automatic CPU speed _works well enough for the majority of users_, and control freaks can always use sudo to manually set the speed, or deliberately shoot themselves in
the foot by making the binary suid root" 

I think he's absolutely right, control freaks should have to do EVERYTHING the hard way... just kidding, freedom of choice guys, that's what it's all about, and don't hinder that. 

OK I'm off my soapbox now. Does ANYONE know of any documentation on what patches are applied to the ubuntu flavor kernels? I don't need to know how to sift through .config's and do diffs to find out on my own, I can do that already. I just want to know if the docs exist. I've searched and come up with nothing.

EDIT: stray carriage return

---

### Post by go_beep_yourself on 2007-11-07
> **go_beep_yourself said:**
> When I compiled a vanilla kernel, I did not have to use make oldconfig to use an existing config file. All I did was copy it from the /boot directory and renamed it to .config. I then made a few changes to that config of mostly getting rid of some things that were not needed for my system. I never had to use make oldconfig. What does that do, and why didn't I need it? I searched the make man page for oldconfig and did not find anything.

Could anyone answer this question? I don't believe a linux distro should be made in a way that it doesn't work with the vanilla kernel. So, am I forced to use an older kernel version because of this? The linux-source package has an older kernel version than the stock Ubuntu kernel, and neither are the newest.

---

### Post by tehtrk on 2007-11-07
> **go_beep_yourself said:**
> Could anyone answer this question? I don't believe a linux distro should be made in a way that it doesn't work with the vanilla kernel. So, am I forced to use an older kernel version because of this? The linux-source package has an older kernel version than the stock Ubuntu kernel, and neither are the newest.

make oldconfig simply copies the settings your current config uses (the settings that are still valid, that is) to the config that the new kernel will use so that if, for example, your old kernel had 802.11 support compiled into it, make oldconfig would enable 802.11 support in the new kernel's config. This helps to avoid forgetting to add, say, reiserfs support and not being able to mount the new root filesystem.

Another thing that make oldconfig does, and you already mentioned it, is present you with new features that are available in the new kernel and ask you if you want those features enabled (you are asked for each individual feature/option). 

I hope this clears things up with make oldconfig. It is a handy tool.

---

### Post by Raven18940 on 2007-11-07
Does anyone know where I can get a copy of the Ubuntu 7.10 kernel source.  I've tried to compile from a vanilla kernel three times now on two seperate machines with no success (they compile but don't run right or at all).  I'd like to start with something I know should work and figure oiut what I'm doing wrong.

EDIT: Nevermind, I found it, wish me luck.

---

### Post by the_unforgiven on 2007-11-08
> **go_beep_yourself said:**
> Could anyone answer this question? I don't believe a linux distro should be made in a way that it doesn't work with the vanilla kernel. So, am I forced to use an older kernel version because of this? The linux-source package has an older kernel version than the stock Ubuntu kernel, and neither are the newest.
I don't think ANY distro would be so badly put together as to not be able to compile a vanilla kernel.
The dependencies of the kernel are listed in the main README of the kernel; as long as all the dependencies are available (either pre-installed or via the repository), it should be possible to build the vanilla kernel on any distro.

Please note that, it's quite easy to build a broken (non-bootable) kernel by messing up with the configuration - say, not including initrd support for BIGMEM kernels or for LVM/RAID root filesystems.

As for how the Ubuntu kernel is configured (which patches are included), you might want to ask the KernelTeam or check up their wiki at: [https://wiki.ubuntu.com/KernelTeam](https://wiki.ubuntu.com/KernelTeam)

HTH ;)

PS: Here is a doc regarding custom compilation of kernel on Ubuntu: [https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild)

---

