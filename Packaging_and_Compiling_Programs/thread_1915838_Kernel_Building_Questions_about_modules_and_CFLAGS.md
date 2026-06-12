---
title: "Kernel Building: Questions about modules and CFLAGS, and other randoms"
date: 2012-01-27
forum: Packaging and Compiling Programs
---

### Post by rwgast on 2012-01-27
Hi im fairly new to developing on linux but catching on quick i like it alot!

Im building custom android kernels, for those not in the know the android kernel is just a fork of the linux kernel and i dont think the build process or directory tree changes much. But if it helps answer some of my questions here is the link to my kernel repo fork. [https://github.com/rwgast/android_kernel_thunderc](https://github.com/rwgast/android_kernel_thunderc)

***So here is my problem my kernels function beautifully. But my modules wont load due to bad symbols. I figured out i need to compile my modules with ***EXTRA_CFLAGS=-fno-pic***. Now exactly how what (make)?file should i be putting that in so only modules compile with that flag. I know i can go in and edit the makefile for each driver but that seems to be the wrong way of doing this.***

I also have a couple more questions about kernel building, im sorry if there is a better forum to add this too.

The command line i use to build my kernel is this, ```
make ARCH=arm CROSS_COMPILE=arm-linux-androideabi-
```
Now if i wanted to make just the kernel and not the modules how what would i be adding to that. I would think there is a way to do this since you can run make modules and it just builds the modules.

Second question i know the kernel is a compressed file is it just gziped? If so which file gzips it? I would like to try some custom command line switches with gzip.

Also this has nothing to do with gcc per-say but when building your kernel especially for a small android device why not just statically compile all the drivers into the kernel? It seems like it would provide a bit faster access than having to load modules, and for the most part fussing with drivers is not an issue on a phone. I can see making features like extra file systems into modules to load later, but most Android ROMs are compiling there wifi and usb stuff into modules.

---

