---
title: "Building latest kernel"
date: 2011-07-23
forum: Packaging and Compiling Programs
---

### Post by Ranko Kohime on 2011-07-23
My setup: Clevo W150HNQ with Intel Sandy Bridge i7-2720QM, 8GB RAM, Intel SSD boot and WD Blue 1TB drive, running Xubuntu Natty.

So I've tried twice now to build a kernel from source, (two different RC's from kernel.org) and both times said kernels panicked on startup.

I have a suspicion that the 2.6.38-etc kernels may have something to do with my infrequent (yet annoying) total system freezes, and I'd like to eliminate the possibility by compiling my own kernel, but that hasn't worked out real well yet.

I'm lost on a great many of the build options in the setup menu that comes in the kernel package.  Not sure what I need, what conflicts, etc...

Can anyone point me in the right direction there?

---

### Post by hawthornso23 on 2011-07-25
[http://duopetalflower.blogspot.com/2011/07/custom-kernel-26393-ubuntu-amd64_15.html](http://duopetalflower.blogspot.com/2011/07/custom-kernel-26393-ubuntu-amd64_15.html)

Link is to a prebuilt kernel based on 2.6.39.3 optimised for i7 processors, which sounds like what you need. The kernel works - I have it on my laptop. The website is also a good place to find up to date instructions for how to go about compiling a kernel.

---

### Post by Ibidem on 2011-07-27
```
make localmodconfig
``` is how I'd suggest starting.  That will get you all the kernel options you need.
I'd strongly recommend not trying to configure it from scratch; it usually takes several tries to get it booting, to say nothing of working right.

---

