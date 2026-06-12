---
title: "Errors while trying to compile the 2.4.32 kernel"
date: 2006-02-18
forum: Packaging and Compiling Programs
---

### Post by K.Mandla on 2006-02-18
Hi. I'm trying to compile the 2.4.32 kernel from kernel.org by following the instructions [here]("http://ubuntuforums.org/showthread.php?t=85064&highlight=kernel+compilation+newbies") and from other, similar howtos.

However, each attempt gives me an error like this. ...

> make[1]: *** [init/main.o] Error 1
make[1]: Leaving directory `/usr/src/linux-2.4.32'
make: *** [stamp-build] Error 2
Is it possible to compile an earlier version of the kernel? I'm using 2.6.12-10-386, but I need an earlier version for another machine that has hardware issues. I'm not using any fancy drivers or modules, and I've modified none of the default options for compiling it.

Any suggestions? I'm still fairly new at compilation, so I'm not sure what's causing that problem or why it's happening. Thanks for your help.

---

### Post by cilynx on 2006-02-18
Welcome to the world of rolling your own kernel...

We're going to need more info than just the last error line though...

Can you give us the 10 or 20 lines above that final error line?

---

### Post by K.Mandla on 2006-02-18
Sure. Let me see what I can come up with here. ...

This is from quite a ways back into the terminal scroll, so I hope it's enough to see what's going on.

```
/usr/bin/make  EXTRAVERSION=-060218  ARCH=i386 \
                     bzImage
make[1]: Entering directory `/usr/src/linux-2.4.32'
gcc -Wall -Wstrict-prototypes -O2 -fomit-frame-pointer -o scripts/split-include scripts/split-include.c
scripts/split-include include/linux/autoconf.h include/config
gcc -D__KERNEL__ -I/usr/src/linux-2.4.32/include -Wall -Wstrict-prototypes -Wno-trigraphs -O2 -fno-strict-aliasing -fno-common -fomit-frame-pointer -pipe -mpreferred-stack-boundary=2 -march=i686 -fno-unit-at-a-time   -DKBUILD_BASENAME=main -c -o init/main.o init/main.c
In file included from /usr/src/linux-2.4.32/include/linux/kernel.h:15,
                 from /usr/src/linux-2.4.32/include/linux/wait.h:13,
                 from /usr/src/linux-2.4.32/include/linux/fs.h:12,
                 from /usr/src/linux-2.4.32/include/linux/capability.h:17,
                 from /usr/src/linux-2.4.32/include/linux/binfmts.h:5,
                 from /usr/src/linux-2.4.32/include/linux/sched.h:9,
                 from /usr/src/linux-2.4.32/include/linux/mm.h:4,
                 from /usr/src/linux-2.4.32/include/linux/slab.h:14,
                 from /usr/src/linux-2.4.32/include/linux/proc_fs.h:5,
                 from init/main.c:15:
/usr/src/linux-2.4.32/include/asm/byteorder.h:14: warning: type qualifiers ignored on function return type
/usr/src/linux-2.4.32/include/asm/byteorder.h:30: warning: type qualifiers ignored on function return type
In file included from /usr/src/linux-2.4.32/include/linux/byteorder/little_endian.h:11,
                 from /usr/src/linux-2.4.32/include/asm/byteorder.h:65,
                 from /usr/src/linux-2.4.32/include/linux/kernel.h:15,
                 from /usr/src/linux-2.4.32/include/linux/wait.h:13,
                 from /usr/src/linux-2.4.32/include/linux/fs.h:12,
                 from /usr/src/linux-2.4.32/include/linux/capability.h:17,
                 from /usr/src/linux-2.4.32/include/linux/binfmts.h:5,
                 from /usr/src/linux-2.4.32/include/linux/sched.h:9,
                 from /usr/src/linux-2.4.32/include/linux/mm.h:4,
                 from /usr/src/linux-2.4.32/include/linux/slab.h:14,
                 from /usr/src/linux-2.4.32/include/linux/proc_fs.h:5,
                 from init/main.c:15:
/usr/src/linux-2.4.32/include/linux/byteorder/swab.h:160: warning: type qualifiers ignored on function return type
/usr/src/linux-2.4.32/include/linux/byteorder/swab.h:173: warning: type qualifiers ignored on function return type
/usr/src/linux-2.4.32/include/linux/byteorder/swab.h:186: warning: type qualifiers ignored on function return type
/usr/src/linux-2.4.32/include/linux/byteorder/swab.h:200: warning: type qualifiers ignored on function return type
In file included from /usr/src/linux-2.4.32/include/linux/prefetch.h:13,
                 from /usr/src/linux-2.4.32/include/linux/list.h:6,
                 from /usr/src/linux-2.4.32/include/linux/wait.h:14,
                 from /usr/src/linux-2.4.32/include/linux/fs.h:12,
                 from /usr/src/linux-2.4.32/include/linux/capability.h:17,
                 from /usr/src/linux-2.4.32/include/linux/binfmts.h:5,
                 from /usr/src/linux-2.4.32/include/linux/sched.h:9,
                 from /usr/src/linux-2.4.32/include/linux/mm.h:4,
                 from /usr/src/linux-2.4.32/include/linux/slab.h:14,
                 from /usr/src/linux-2.4.32/include/linux/proc_fs.h:5,
                 from init/main.c:15:
/usr/src/linux-2.4.32/include/asm/processor.h:75: error: array type has incomplete element type
make[1]: *** [init/main.o] Error 1
make[1]: Leaving directory `/usr/src/linux-2.4.32'
make: *** [stamp-build] Error 2

```
I would offer some guesses as to why it's happening, but I would just be revealing my own ignorance, and I'm chock full on humility these days. :mrgreen: 

Thanks again.

---

### Post by cilynx on 2006-02-18
Let's take a step back.

You're building a kernel for a different machine.  Is the other machine live at the moment?  Is it running Ubuntu as well or is it a different flavor?  

Basically, why are you building a kernel for the other machine in the first place?  Maybe there's an easier way to go about things...

---

### Post by K.Mandla on 2006-02-18
Well, you're right, there are a few things going on here at once. 

First, the target machine is an old Pentium II-era laptop. It's running at somewhere in between 200Mhz and 475Mhz, which means that compiling a kernel would take several hours.

On the other hand, I have an XPS M170 sitting to the left of it, running ten times as fast. Compiling on that machine takes under 30 minutes for the latest kernel, if I let it sit and do nothing else.

The little laptop needs to step back in kernels because it has some hardware issues with PCMCIA ports that I've traced to the 2.6-series kernel. For example, there is _no_ communication with the PCMCIA ports in 2.6.9, 2.6.10 or 2.6.15. 

However, if I install a stripped-down version of Slackware 10.2 on it, it suddenly springs to life. I can cruise the Internet and e-mail to my heart's desire. Slack is running the 2.4.31 kernel.

But I don't like Slack. I find it a bit cumbersome. I can use it, since I spend most of my time in XFCE on that machine, but it's a little irritating. I prefer Ubuntu and I'd love to install Xubuntu on that, but it's going to need that 2.4.31 (or .32, really) kernel to get the job done.

So you can see my issue. I could install Ubuntu server on the machine but I'd still need to get at the build-essential and other packages that don't come with the standard install. Now I'm back to the original problem ... I can't get at the Internet to download those. I could pick through the dependencies and copy them over via USB flash, but that would add hours and hours to a task that's going to need to run overnight anyway.

So I'm trying to avoid turning a 28-minute chore into a two- or three-day marathon. I'm willing to call it a shortcut, but can you blame me? ;) 

If you can suggest something else, I'm willing to try it. Just don't say, "Stick with Slack." :D

---

### Post by cilynx on 2006-02-18
Why not install Hoary on it?  To the best of my knowledge, Hoary uses 2.4.27.  You can probably even upgrade most of the way to Breezy without updating the kernel.  Just don't expect hotplug to work (as if you would expect that out of a PII laptop...).

---

### Post by K.Mandla on 2006-02-19
Excellent! I should've thought to look at past versions of Ubuntu. Thanks! I'll try it when I get home from work. Cheers! :mrgreen:

---

