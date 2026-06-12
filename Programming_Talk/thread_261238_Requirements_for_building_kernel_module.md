---
title: "Requirements for building kernel module"
date: 2006-09-20
forum: Programming Talk
---

### Post by rdilliker on 2006-09-20
Hi,

I'm trying to learn how to write device drivers for Linux and am reading O'Reilly's book on the subject. I am just starting out but am a little bit confused because of the following excerpt:

> Regardless of the origin of your kernel, building modules for 2.6.x requires that you have a configured and built kernel tree on your system. This requirement is a change from previous versions of the kernel, where a current set of header files was sufficient. 2.6 modules are linked against object files found in the kernel source tree; the result is a more robust module loader, but also the requirement that those object files be available. 


1)From reading some other threads on these forums it seems that having the linux kernel headers _is_ sufficient. What am I missing here that is causing confusion?

2) There is a linux-kernel-headers package and a linux-headers package. From what I can tell linux-kernel-headers has the headers for user space applications whereas linux-headers has the headers needed for kernel modules. If this is true, isn't the naming of the packages a bit confusing? I would think linux-kernel-headers means for kernel space applications.

Thanks for any help.

Update: So I was able to successfully build and load the "hello world" kernel module in the book by just getting the linux-headers package so this confirms that what the book says seems to be wrong. I don't need a built kernel source tree. Anyone care to answer my questions above?

---

### Post by rdilliker on 2006-09-20
Anyone?

---

### Post by az on 2006-09-22
> **rdilliker said:**
> 
1)From reading some other threads on these forums it seems that having the linux kernel headers _is_ sufficient. What am I missing here that is causing confusion?

The book is wrong; that is confusing you.


> **rdilliker said:**
> 
2) There is a linux-kernel-headers package and a linux-headers package. From what I can tell linux-kernel-headers has the headers for user space applications whereas linux-headers has the headers needed for kernel modules. If this is true, isn't the naming of the packages a bit confusing? I would think linux-kernel-headers means for kernel space applications.

  
Linux-kernel-headers used to be part of libc6-dev.  It was split in Debian to make more sense for running Debian on other kernels like BSD, Solaris, Hurd, etc...  I think the Hurd would have an equivalent hurd-kernel-headers package which would abstract the hurd kernel-specific functions for libc6, for example.

---

### Post by dhpe on 2006-09-22
Hello, rdilliker

I am having exactly the same problem that you had. Only that I cannot get it work.

Could you explain exactly how you are building the "hello world" module?

I installed linux-headers-2.6.15-27 and wrote a Makefile containing only "obj-m := hello.o" for building "hello.c". However, when executing *make -C /usr/src/linux-headers-2.6.15-27-686 m=`pwd` modules* I only get:

> make[1]: *** No rule to make target `arch/i386/kernel/msr.c', needed by `arch/i386/kernel/msr.o'.  Stop.
make: *** [arch/i386/kernel] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.15-27-686'

Previously I built 2.6.15 kernel, but, I'm assuming, as it is not the same as 2.6.15-27 (which I'm running), I could not *insmod* it - - back then it (the hello world module) was built succesfully, however. Now that I'm trying with headers, I cannot even build it.

I'd appreciate any help to get it work.

---

### Post by rdilliker on 2006-09-23
> **dhpe said:**
> Hello, rdilliker

I am having exactly the same problem that you had. Only that I cannot get it work.

Could you explain exactly how you are building the "hello world" module?

I installed linux-headers-2.6.15-27 and wrote a Makefile containing only "obj-m := hello.o" for building "hello.c". However, when executing *make -C /usr/src/linux-headers-2.6.15-27-686 m=`pwd` modules* I only get:



Previously I built 2.6.15 kernel, but, I'm assuming, as it is not the same than 2.6.15-27 (which I'm running), I could not *insmod* it - - back then it (the hello world module) was built succesfully, however. Now that I'm trying with headers, I cannot it even build it.

I'd appreciate any help to get it work.

From the make error it seems that there is no file arch/i386/kernel/msr.c but the makefile expects one there. I installed the linux-headers package for amd64-generic and the module built fine and I could load it into the kernel too. I'm out of town until tomorrow so I can help you more when I get to my Linux machine.

---

