---
title: "Install hardware specific issues - 32 vs 64 bit"
date: 2011-09-20
forum: New to Ubuntu
---

### Post by Denver Dave on 2011-09-20
I guess it is about time I actually read the directions - working on this:
New to Ubuntu - start here:
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

My Q - 
I'm thinking I'm installing to a USB and running on various PCS.  Seems to work on 4 PCs I've tested, but wondering about various hardware dependencies.

- First off is the question of whether to get the 64 bit or 32 bit install. One of my processors is an "AMD Athlon(tm) 64 Processor".  One would imply from the name, a 64 bit processor, but every test I've run says 32 bit.  Confusion is generated also from separating the processor from installed XP and ubuntu and maybe Windows 7.  My suspicion is that I've installed the 32 bit and I could have installed the 64 ubuntu - maybe the Official ubuntu book comes with 32 bit disk?  Ordered 64 bit disk, will see if it runs (from osdisc, don't have launchpad yet).

- when installing says configuring hardware.  Does this imply it is detecting hardware?  If so,what are the ramifications of using USB install on different PCs.  The experience of taking my operating system with me on a USB is pretty intriguing and seems to work.

When created USB Stick on Windows 7 PC, then during boot USB on XP PC - has an option to select the windows 7 loader.  Haven't tried this yet to see what happens (not sure I dare), but obviously, some hardware or at least installed software was detected.

Does the 64 bit version run faster?  Will the 32 bit version run on 64  bit processor and the reverse?

Observations?  Thanks - starting again at the beginning  - multi threaded of course.

= = = = = 
Would also like to add that I'd never dream of asking these Q's and install operating system different ways with XP or Vista - not sure I even could.

---

### Post by seawolf167 on 2011-09-20
> **Denver Dave said:**
> I guess it is about time I actually read the directions - working on this:
New to Ubuntu - start here:
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

My Q - 
I'm thinking I'm installing to a USB and running on various PCS.  Seems to work on 4 PCs I've tested, but wondering about various hardware dependencies.

- First off is the question of whether to get the 64 bit or 32 bit install. One of my processors is an "AMD Athlon(tm) 64 Processor".  One would imply from the name, a 64 bit processor, but every test I've run says 32 bit.  Confusion is generated also from separating the processor from installed XP and ubuntu and maybe Windows 7.  My suspicion is that I've installed the 32 bit and I could have installed the 64 ubuntu - maybe the Official ubuntu book comes with 32 bit disk?  Ordered 64 bit disk, will see if it runs (from osdisc, don't have launchpad yet).

If you are going to use a portable external hard drive on multiple machines, use the x86 (32bit) version to ensure it works on all machines.

If, however, you are only using on a single machine which you know to be 64bit capable, then use the x86_64 (64bit) version in order to get the most out of your hardware, etc.

> **Denver Dave said:**
> - when installing says configuring hardware.  Does this imply it is detecting hardware?  If so,what are the ramifications of using USB install on different PCs.  The experience of taking my operating system with me on a USB is pretty intriguing and seems to work.

Basically just looking for, setting up drivers, etc. As long as you have an internet connection if you plug into a machine with different hardware that requires different drivers, you will be able to download and run those new drivers.

> **Denver Dave said:**
> When created USB Stick on Windows 7 PC, then during boot USB on XP PC - has an option to select the windows 7 loader.  Haven't tried this yet to see what happens (not sure I dare), but obviously, some hardware or at least installed software was detected.

Not sure what you mean? You have a Windows 7 boot USB? Or a Ubuntu boot USB that you created on Windows 7 with something like [UNetbootin]("http://unetbootin.sourceforge.net/")?

> **Denver Dave said:**
> Does the 64 bit version run faster?  Will the 32 bit version run on 64  bit processor and the reverse?

The very basics: 64 bit can handle more threads and can address more RAM, essentially, yes it will run faster for programs designed to take advantage of the 64bit systems' capabilities.

32bit will run on 64bit machines, but 64bit WILL NOT run on 32bit machines.

---

### Post by Denver Dave on 2011-10-04
I ordered a 64 bit ubuntu disk and tried it on my laptop and older desktop.  Both the 64 bit ubuntu disk and disk from the book "The Official ubuntu book" work on both PCs.  So this raises the question whether the disk from the book is 32 bit or 64 bit - it does not say.

I've seen various cryptic ways to test if the hardware is 32 or 64 bit, but I haven't seen a way to test if the operating system being  run is 32 or 64 bit.   Is here a way to determine if the operating system is 64 bit?

I don't see an obvious difference when runnnig - is there a simple test to show the power of the 64 bit?

---

### Post by seawolf167 on 2011-10-04
To determine if it is 32bit (x86) or 64bit (x86_64), type in the following at a terminal

```
uname -a
``````
Linux yuna 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 **x86_64** GNU/Linux
```the ending part will show what your OS is (my laptop - the above - is 64bit)

---

