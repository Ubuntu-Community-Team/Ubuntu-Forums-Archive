---
title: "Compiling 2.4.26"
date: 2006-03-12
forum: Packaging and Compiling Programs
---

### Post by Mike_Leash on 2006-03-12
i'm creating openmosix cluster. 
trying to compile 2.4.26 kernel from kernel.org and latest openmosix 2.4.26 patch from sourceforge.net

every time I type 

#make dep bzImage modules modules_install

this comes out:

> 
In file included from /usr/src//linux-2.4.26/include/linux/kernel.h:15,
                 from /usr/src/linux-2.4.26/include/linux/wait.h:13,
                 from /usr/src/linux-2.4.26/include/linux/fs.h:12,
                 from /usr/src/linux-2.4.26/include/linux/capability.h:17,
                 from /usr/src/linux-2.4.26/include/linux/binfmts.h:5,
                 from /usr/src/linux-2.4.26/include/linux/sched.h:9,
                 from /usr/src/linux-2.4.26/include/linux/mm.h:4,
                 from /usr/src/linux-2.4.26/include/linux/slab.h:14,
                 from /usr/src/linux-2.4.26/include/linux/proc_fs.h:5,
                 from init/main.c:15:
/usr/src/linux-2.4.26/include/asm/byteorder.h:14: warning: type qualifiers ignored on function return type
/usr/src/linux-2.4.26/include/asm/byteorder.h:30: warning: type qualifiers ignored on function return type
In file included from /cluster/linux-2.4.26/include/linux/byteorder/little_endian.h:11,
                 from /usr/src//linux-2.4.26/include/asm/byteorder.h:65,
                 from /usr/src/linux-2.4.26/include/linux/kernel.h:15,
                 from /usr/src/linux-2.4.26/include/linux/wait.h:13,
                 from /usr/src/linux-2.4.26/include/linux/fs.h:12,
                 from /usr/src/linux-2.4.26/include/linux/capability.h:17,
                 from /usr/src/linux-2.4.26/include/linux/binfmts.h:5,
                 from /usr/src/linux-2.4.26/include/linux/sched.h:9,
                 from /usr/src/linux-2.4.26/include/linux/mm.h:4,
                 from /usr/src/linux-2.4.26/include/linux/slab.h:14,
                 from /usr/src/linux-2.4.26/include/linux/proc_fs.h:5,
                 from init/main.c:15:
/usr/src/linux-2.4.26/include/linux/byteorder/swab.h:160: warning: type qualifiers ignored on function return type
/usr/src/linux-2.4.26/include/linux/byteorder/swab.h:173: warning: type qualifiers ignored on function return type
/usr/src/linux-2.4.26/include/linux/byteorder/swab.h:186: warning: type qualifiers ignored on function return type
/usr/src/linux-2.4.26/include/linux/byteorder/swab.h:200: warning: type qualifiers ignored on function return type
In file included from /usr/src/linux-2.4.26/include/linux/prefetch.h:13,
                 from /usr/src/linux-2.4.26/include/linux/list.h:6,
                 from /usr/src/linux-2.4.26/include/linux/wait.h:14,
                 from /usr/src/linux-2.4.26/include/linux/fs.h:12,
                 from /usr/src/linux-2.4.26/include/linux/capability.h:17,
                 from /usr/src/linux-2.4.26/include/linux/binfmts.h:5,
                 from /usr/src/linux-2.4.26/include/linux/sched.h:9,
                 from /usr/src/linux-2.4.26/include/linux/mm.h:4,
                 from /usr/src/linux-2.4.26/include/linux/slab.h:14,
                 from /usr/src/linux-2.4.26/include/linux/proc_fs.h:5,
                 from init/main.c:15:
/usr/src/linux-2.4.26/include/asm/processor.h:75: error: array type has incomplete element type
In file included from /usr/src/linux-2.4.26/include/hpc/hpctask.h:13,
                 from /usr/src/linux-2.4.26/include/linux/sched.h:33,
                 from /usr/src/linux-2.4.26/include/linux/mm.h:4,
                 from /usr/src/linux-2.4.26/include/linux/slab.h:14,
                 from /usr/src/linux-2.4.26/include/linux/proc_fs.h:5,
                 from init/main.c:15:
/usr/src/linux-2.4.26/include/hpc/defs.h:86: error: array type has incomplete element type
make: *** [init/main.o] Error 1



i'm using gcc 3.4.3-9

thanks

---

### Post by evilgold on 2006-03-12
I dont think its a good idea to run a 2.4 kernel with ubuntu. If you really want open mosix your gonna have to go with gentoo, or and RPM based distro. 

I'll try to come back to this tread later and see if i can help you with that build error later, but (sigh) i have to be at work in about 5 minutes.

---

### Post by ajt on 2007-01-01
I've been looking into running an openMosix 2.4 kernel with Ubuntu recently because I'm about to upgrade a Beowulf cluster from Red Hat 9.0 to a Debian-based Linux distribution and the openMosix 2.6 kernel is still an alpha release. The latest clusterknoppix 2.4.27 openMosix kernel will install and run under Ubuntu 6.06.1 LTS with a bit of manual post-install work:

[http://public.planetmirror.com/pub/clusterknoppix/kernel-image-2.4.27-om-20040808_10.00.Custom_i386.deb]("http://public.planetmirror.com/pub/clusterknoppix/kernel-image-2.4.27-om-20040808_10.00.Custom_i386.deb")

The main problem is that udev requires a 2.6 kernel, so you have to populate /dev manually using (/dev/MAKEDEV).

There are problems recompiling the 2.4.26 and 2.4.27 kernels with the 6.06 LTS gcc and binutils, but most of the problems are resolved if you install gcc-3.3 and edit the kernel Makefile to change "gcc" to "gcc-3.3". The latest 2.4.34 Linux kernel from kernel.org compiles OK with gcc-4.0.

There are further problems with the 2.4.26/27 kernels and "as" from the 6.06.1 LTS binutils because the "movl" assembly instruction is used in several  places instead of "movw". This can easily be resolved by editing a few source files.

BTW, these problems also occur when trying to compile the 2.4.26/27 openMosix kernels under Debian Etch. I'm, optimistically, hoping I can upgrade to the 2.6 openMosix kernel in due course. However, I do think it's practical to run a 2.4 kernel under Ubuntu 6.06.1 LTS.

Please send mailto:ajt@rri.sari.ac.uk if you're interested in this.

    Tony.

---

