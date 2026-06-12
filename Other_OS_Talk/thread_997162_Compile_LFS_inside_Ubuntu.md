---
title: "Compile LFS inside Ubuntu?"
date: 2008-11-29
forum: Other OS Talk
---

### Post by Peter Frank on 2008-11-29
I want to have a try at Linux from Scratch, but I would really like the comfort of compiling it from within my Ubuntu install. Will that be possible? (i.e. does Ubuntu have the right versions of GCC etc. required for compiling LFS?)

---

### Post by smartboyathome on 2008-11-29
I would say if you want to build it inside Ubuntu, use a virtual machine and virtualize the LFS livecd. That way minimizes what can go wrong.

---

### Post by LinuxGuy1234 on 2008-11-29
> **Peter Frank said:**
> I want to have a try at Linux from Scratch, but I would really like the comfort of compiling it from within my Ubuntu install. Will that be possible? (i.e. does Ubuntu have the right versions of GCC etc. required for compiling LFS?)

I would suggest, like smartboyathome suggested, use a virtual machine. But, install Ubuntu first then do:
```
sudo apt-get install gcc binutils libc6-dev
```
...and get your dependencies for compiling.
Make sure you have at least three partitions before starting.
You may now compile LFS using the empty-partition-soon-to-be-LFS-partition.

---

### Post by Sorivenul on 2008-11-29
Definitely possible, but I agree with the virtual machine suggestion.  VirtualBox works fine for me whenever I've used it to do this same task.
My method goes like this:
- Download LFS LiveCD ISO
- Create Virtual Machine in VirtualBox with the LFS LiveCD ISO mounted as the CD
- Follow the directions to build [ALFS (Automated Linux From Scratch)]("http://www.linuxfromscratch.org/alfs/") from the LiveCD.  Directions can be found in the section "AUTOMATING THE BUILD" [here]("http://www.linuxfromscratch.org/livecd/documentation.html").
- When the build is done, reboot, unmount the ISO, and you have your system!

---

