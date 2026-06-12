---
title: "Looking for gcc-arm-none-eabi in all the wrong places"
date: 2016-08-12
forum: Packaging and Compiling Programs
---

### Post by john_ladasky on 2016-08-12
Hello everyone,

My Ubuntu 14.04 installation was showing its age.  Specifically, something happened to Unity and I couldn't see my launcher.  I couldn't fix the problem through the terminal, despite reading many web pages.  I wanted to upgrade to 16.04 anyway, so I finally went ahead with that.  I did a clean reinstall to make sure that I cleared out any old config files.  While that worked, I also wiped out all of my applications.

One of the things that I broke was gcc-arm-none-eabi, a cross compiler for embedded ARM CPU's.  I spent about a week setting that up, around a year ago.  It wasn't simple.  But that was on 14.04, and I'm hoping that I can do it again with less trouble on 16.04.

Using Synaptic, I installed gcc-arm-none-eabi.  I have version 15:4.9.3+svn231177-1.  Looking over the list of Installed Files, I see that the package installed files in /usr/bin, /usr/lib/gcc, /usr/share/doc, and /usr/share/lintian.

I then attempted to compile and link a simple test application for my embedded system as follows:

```
j...@...x:~/src/nRF52_SDK_0.9.2_dbc28c9/examples/peripheral/blinky/pca10036/blank/armgcc$ make


rm -rf _build
echo  Makefile
Makefile
mkdir _build
Compiling file: system_nrf52.c
make: /usr/local/gcc-arm-none-eabi-4_9-2015q1/bin/arm-none-eabi-gcc: Command not found
Makefile:133: recipe for target '_build/system_nrf52.o' failed
make: *** [_build/system_nrf52.o] Error 127


j...@...x:~/src/nRF52_SDK_0.9.2_dbc28c9/examples/peripheral/blinky/pca10036/blank/armgcc$ echo $PATH

/home/john/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin

```
So it looks like **make** went looking for the GCC cross compiler in /usr/local/gcc-arm-none-eabi-4_9-2015q1/bin.  Why?  This is a new, clean install of 16.04.  This is not a folder that was specified in the gcc-arm-none-eabi package.  This is also not a folder that is included in my $PATH.  I don't know how Ubuntu decided to go looking for a non-existent folder.  I also don't know why /usr/bin is not in my default $PATH.  Of course I'm going to try adding it. And while that may fix my problem, I don't understand the reason that things come out of the box set up the way that they are.

---

### Post by steeldriver on 2016-08-12
Please post the contents of the relevant Makefile

FYI /usr/bin is in your path - between /usr/sbin and /sbin

---

