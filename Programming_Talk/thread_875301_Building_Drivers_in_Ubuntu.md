---
title: "Building Drivers in Ubuntu"
date: 2008-07-30
forum: Programming Talk
---

### Post by riluve on 2008-07-30
I am a Linux source noobie and I would like to learn how to build drivers under Ubuntu, but the only instructions I can find for building drivers basically requires the entire kernel source.

I can build kernel source under Ubuntu 8.05, but I have difficulty installing the kernel and I can't find much help to install it.  Rather, the Ubuntu documentation says - don't build kernel source just to build a driver, but it doesn't provide instructions to do that either.

So the driver I compile with my kernel is not compatible with the installed kernel and I can't install either the new kernel or the resulting new driver.

I really don't want to install some other distribution for this "simple" task, but . . .

Well does anyone know a simple solution under Ubuntu? (That is, how to build a driver in Ubuntu, without using the full kernel source)

---

### Post by mike_g on 2008-07-30
Well tbh I generally wouldent describe creating drivers as a "simple" task.


[Modprobe](http://linux.die.net/man/8/modprobe) is a shell command that allows you to add compiled modules to the kernal.

---

### Post by KedDeK on 2008-07-30
Read [http://tldp.org/LDP/lkmpg/2.6/html/index.html](http://tldp.org/LDP/lkmpg/2.6/html/index.html)

Of course you need to have linux kernel headers installed.

---

### Post by riluve on 2008-07-31
> **mike_g said:**
> Well tbh I generally wouldent describe creating drivers as a "simple" task.


[Modprobe](http://linux.die.net/man/8/modprobe) is a shell command that allows you to add compiled modules to the kernal.

Haha - well I do BIOS and UEFI, so a linux driver is really the same thing in  a new environment.

But yeah I have been unsuccessfully using Modprobe.  The headers linked with the driver are incompatible unless it is compiled with the same version of the kernel that is executing - even in the simplest driver.  There seems to be ways to override this incompatibility, but I want a way to do it right, not just a hack.

But like I said, the Ubuntu kernel documentation tells me not to build the whole kernel just for a new driver, but then it leaves me out in the cold.

---

### Post by riluve on 2008-07-31
> **KedDeK said:**
> Read [http://tldp.org/LDP/lkmpg/2.6/html/index.html](http://tldp.org/LDP/lkmpg/2.6/html/index.html)

Of course you need to have linux kernel headers installed.

Hey - great link and thnx - but that really only covers what I have already been doing.  But from what you are saying, I need to figure out how to get the Ubuntu Kernel headers and then figure out how to link against them (as opposed to linking against the entire kernel source).

I'll look back through that document and see if it covers that aspect.  My initial scan however, did not reveal this type of building/linking.

---

### Post by mssever on 2008-07-31
Have you installed the proper linux-headers-* package for your machine? That should give you the proper kernel headers.

---

### Post by riluve on 2008-08-01
> **mssever said:**
> Have you installed the proper linux-headers-* package for your machine? That should give you the proper kernel headers.

OK - so yeah the headers were there, but I didn't want to dig through the make files to figure out the entire structure and then make my own build environment - maybe i'll come back to that.

Anywho, after researching every decent alternative, I just decided to get the actual Ubuntu kernel source and build/link against it.  So I am trying that now, but it seems like it should work.

---

### Post by riluve on 2008-08-02
OK - I had some time to make some progress, thnx for everyones help!

Now I have 2 problems / concerns:

#1 - I am able to use insmod/rmmod and even modinfo, but if I try modprobe - it fails (reporting the module was not found).  I tried both relative and absolute paths, both with and without sudo, so this is kinda crazy to me.

#2 - When my driver installs I get the following error:
[FONT="System"]no version for "struct_module" found: kernel tainted.[/FONT]

Now - I actually could never get vmlinux to build fully, with Ubuntu source - it failed somewhere in network support, but it seems to me all of the rudimentary data structures should have been created.  So, I don't think this causes the 2nd error, but I am going to look into that.

My immediate question is this some Ubuntu specific thing and/or how critical is it (the "struct_module" version error)?

.

---

