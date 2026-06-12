---
title: "(Probably) Stupid question on kernel source"
date: 2007-04-23
forum: Programming Talk
---

### Post by the_dark_light on 2007-04-23
This is probably a stupid question, but what the hey (Admitting that I'm a noob is the first step)

I need to build a new kernel module (the sqcam driver for kernel 2.6, to get a cheap and nasty camera working as a webcam) but it needs the Kernel source.

When trying to find the kernel source in Synaptic, I found 2 packages:

linux-source
linux-source-2.6.20

The difference seems to be that one is 2.6.20-15.14 and the other is 2.6.20-15.27

Are these the right packages, and which one do I need to install? :confused:

---

### Post by simonn on 2007-04-23
The following will tell you the release of your kernel.

```

uname -r

```

I suspect that you only need the kernel header, not the full source:

linux-headers-2.6.20
linux-headers-2.6.20-{generic,386,686,K7 etc}
linux-headers-{generic,386,686,K7 etc}

---

### Post by the_dark_light on 2007-04-23
thanks simonn, it's making some progress now.  Unfortunately, it's running in to a few problems, it refuses to compile.

Here's how it starts:

make -C /usr/src/linux-headers-2.6.20-15/ SUBDIRS=/home/dan/sqcam_driver_for_kernel_2_6 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15'

  WARNING: Symbol version dump /usr/src/linux-headers-2.6.20-15/Module.symvers
           is missing; modules will have no dependencies and modversions.

it goes on to produce a large number of the following style errors:

/home/dan/sqcam_driver_for_kernel_2_6/usbvideo.h:243: error: field ‘vchan’ has incomplete type
/home/dan/sqcam_driver_for_kernel_2_6/usbvideo.h:268: warning: ‘struct video_window’ declared inside parameter list
/home/dan/sqcam_driver_for_kernel_2_6/usbvideo.h:268: warning: its scope is only this definition or declaration, which is probably not what you want
/home/dan/sqcam_driver_for_kernel_2_6/usbvideo.h:277: error: field ‘vdt’ has inc

unfortunately threre are too many to list.  Finally:

/home/dan/sqcam_driver_for_kernel_2_6/sq905.c:1364: warning: implicit declaration of function ‘page_address’
make[2]: *** [/home/dan/sqcam_driver_for_kernel_2_6/sq905.o] Error 1
make[1]: *** [_module_/home/dan/sqcam_driver_for_kernel_2_6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [module] Error 2

I don't suppose anyone can suggest a way to remedy this? (Gods, I'm such a n00b :( )

---

### Post by simonn on 2007-04-23
What did uname -s return?

If it was 2.6.20-15-generic, try:

> 
make -C /usr/src/linux-headers-2.6.20-15-generic SUBDIRS=/home/dan/sqcam_driver_for_kernel_2_6 modules


If it was 2.6.20-15-386, replace generic with 386 etc.

---

### Post by the_dark_light on 2007-04-23
"uname -s" returned: "Linux"

---

### Post by simonn on 2007-04-23
Sorry, mean uname -r

---

### Post by the_dark_light on 2007-04-24
running "uname -r" returns the following:

2.6.20-15-generic

(fortunately there don't seem to have been any kernel updates complicating things)

---

### Post by anando on 2008-03-01
hi i have another stupid question on this - can I delete the kernel source directory after building and installing it ? i recently built the 2.22.9 kernel with SLAB (so that it suspends nicely with my ati x1600 card on a macbook pro c2d). i followed the instructions on this blog [http://blog.vaxius.net/?p=19](http://blog.vaxius.net/?p=19) . after the debs were created, i dpkg installed them. now i find that my src directory is a whopping 2.5 GB and that there is not much space left in my / partition. so - to the more experienced people here - can i safely delete the src directory /usr/src/linux ?

many thanks in advance,
anand.

---

### Post by dwhitney67 on 2008-03-01
The source code is not 2.5GB.  It is probably a boat-load of object files and images that are responsible for that bloat.

Goto you /usr/src/linux directory and run 'make mrproper'.  This should clean up the source directory.

If you really want to get rid of the source code, then yes, it is safe to remove it.  Personally though, I would keep it in case you need to compile again.

---

### Post by anando on 2008-03-03
> **dwhitney67 said:**
> 

Goto you /usr/src/linux directory and run 'make mrproper'.  This should clean up the source directory.



That worked and got rid of all the bloat - more than 2 GB of it. Many thanks for your help.

- Anando.

---

### Post by lucasrichter on 2008-03-12
Ta dwhitney67. That was exactly what I needed to know :)

---

