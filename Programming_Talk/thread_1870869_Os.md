---
title: "Os"
date: 2011-10-28
forum: Programming Talk
---

### Post by 7cardcha on 2011-10-28
How would you go about writing your own OS in C using the linux kernel. I know that an OS is mostly a kernel but still. Any ideas(I would write commands QUI etc. I have good knowledge of C/C++/Python
)

---

### Post by V for Vincent on 2011-10-28
I'd start by checking out minix3.org. The original minix helped Linus get started, in any case.

---

### Post by 7cardcha on 2011-10-28
I want to take the linux kernel and write the rest of the OS tools(commands etc etc) and packaging software with it. How can I do this LFS is ok BUT THEY DON'T HAVE A GOOD GUIDE I am know C/C++
They only pre-written thing I want to use is the linux kernel. NOTHING MORE.

---

### Post by 11jmb on 2011-10-28
Ambitious :D

Perhaps you would consider making your own GNU/Linux flavor first. There is a lot of code that needs to be written to get an operating system working. One way to approach this would be starting with the kenrel, GNU base system, and a simple desktop, then start peeling back the layers once you get it working.

---

### Post by haqking on 2011-10-28
[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

and what is wrong with the guide [http://www.linuxfromscratch.org/lfs/view/stable/](http://www.linuxfromscratch.org/lfs/view/stable/)

If you cant build a system from that using that guide, i highly doubt you will manage to build your own system

---

### Post by Liiiim on 2011-10-28
Will you be writing your own C library, or are you counting that as part of the kernel (it's not, but writing your own C library would be an enormous undertaking).

If you just want to implement stuff like 'cd', 'echo', etc., take a look at the man pages - those should be all the "guides" you'll need.

---

### Post by lisati on 2011-10-28
Threads merged.

---

### Post by 7cardcha on 2011-10-28
Ok Ill stop with LFS. Then come back when I am done with that.

---

### Post by MG&amp;TL on 2011-10-28
And the excellent MikeOS:

[http://mikeos.berlios.de/]("http://mikeos.berlios.de/")

You might also want to learn how to write drivers for things in C/assembly. If your keyboard doesn't work on your OS, you're kinda screwed.

---

### Post by gsmanners on 2011-10-28
> **MG&TL said:**
> You might also want to learn how to write drivers for things in C/assembly. If your keyboard doesn't work on your OS, you're kinda screwed.

This is why you do all that low level stuff in an emulator first, then build on top of your system once you have the OS and the toolchain installed.

---

### Post by MG&amp;TL on 2011-10-28
...sure. Sorry, my point was that if you can't code the keyboard, then making any further progress is difficult. Right?

And forgive my ignorance, but would not running in a VM throw some problems up when you migrate, as all the low-level memory management *was* dealt with by the host OS. ?

I got my limited knowledge from an outdated book about device drivers for UNIX, so I have a very limited idea what everyone is on about. I was just suggesting that learning to code for devices was a good idea.

Or you might want to build on a *nix kernel, and save yourself the effort of dealing with all that stuff, and get on with the fun things like desktops.

---

### Post by Liiiim on 2011-10-28
I think you're misunderstanding what a VM does.  It totally emulates a computer - the BIOS, devices, etc.  To an OS running in the VM, the host OS might as well not even exist.  Of course VMs aren't perfect and there will be some discrepancies between how the VM behaves and how real hardware behaves, but for the most part running an OS in a VM is like running it on a real computer.

Before you can write device drivers you need a certain amount of foundation to work off of.  You would probably at least want to be in protected mode with some basic memory management. Writing that stuff can be fairly difficult and involved, depending on what kind of tools you'll want available when writing the device drivers.

Alternatively you could rewrite drivers for some *nix OS, so that foundation would already exist.  That might offer some good practice with low-level programming.

---

### Post by MG&amp;TL on 2011-10-28
> **Liiiim said:**
> I think you're misunderstanding what a VM does.  It totally emulates a computer - the BIOS, devices, etc.  To an OS running in the VM, the host OS might as well not even exist.  Of course VMs aren't perfect and there will be some discrepancies between how the VM behaves and how real hardware behaves, but for the most part running an OS in a VM is like running it on a real computer.



Cool. Thanks, Liiiim.

---

