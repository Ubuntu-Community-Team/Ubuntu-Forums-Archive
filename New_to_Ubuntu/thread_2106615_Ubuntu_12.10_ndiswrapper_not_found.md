---
title: "Ubuntu 12.10 ndiswrapper not found"
date: 2013-01-19
forum: New to Ubuntu
---

### Post by sterlbomb on 2013-01-19
Trying to get my WNDA3100v2 wireless netgear card working on Ubuntu 12.10.

Found several sets of instructions but am running into some problems, I have been following this thread [http://ubuntuforums.org/showthread.php?t=1964173](http://ubuntuforums.org/showthread.php?t=1964173), but when I try to install the drivers for the card using "Windows Wireless Drivers" I get the following error: "Module ndiswrapper not found". 

So next I started trying to solve that error and have made sure I have all the ndiswrapper packages installed along with neccessary addons, then when trying to start it I still get the following error:

sterlbomb@sterlbombs-PC:~$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.

I heard it was a problem with ndiswrapper 1.57 on ubuntu 12.10 so I tried to download ndiswrapper 1.58, then install and compile it, but as you can see from my shell output I'm running into another problem:

MyUsername-PC:~$ cd /usr/src/modules/ndiswrapper/
MyUsername-PC:/usr/src/modules/ndiswrapper$ sudo make
[sudo] password for MyUsername:
Makefile:36: *** Cannot find kernel version in /lib/modules/3.5.0-17-generic/build, is it configured?.  Stop.
MyUsername-PC:/usr/src/modules/ndiswrapper$

So the next problem seems to be that the kernel version isn't being mentioned and I can't seem to find much data online. I tried getting the headers for 3.5.0-17-generic but that didn't work either. Apparently the entire 3.5.0-17-generic/build folder is missing.... not sure why or how to get the content that its looking for. any help would be greatly appreciated.

---

### Post by ajgreeny on 2013-01-19
I don't know if you found this site, but if not have a good look at section 4 of [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) with compilation instructions for the latest version and all the additional packages you will need.

---

### Post by sterlbomb on 2013-01-21
Thanks for the response ajgreeny, I did find that site and have tried to compile the latest version of ndiswrapper, but this is the following error I get when trying to follow the 2nd part of this step:[I] 

4.1. Install kernel headers[/I][I] 
[LIST]
[*]From a Terminal, run: 
sudo apt-get install linux-headers-$(uname -r) and run the following for the dependencies: 
sudo apt-get install dh-make fakeroot gcc-3.4 build-essential
[/LIST]
[/I]I get the following: 

[I]#sudo apt-get install dh-make fakeroot gcc-3.4 build-essential
ERROR: ld.so: object 'libfakeroot-sysv.so' from LD_PRELOAD cannot be preloaded: ignored.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gcc-3.4
E: Couldn't find any package by regex 'gcc-3.4'[/I]

Then when trying to compile the latest version of ndiswrapper using *sudo make* I still get the error: [I]

Makefile:36: *** Cannot find kernel version in /lib/modules/3.5.0-17-generic/build, is it configured?.  Stop.

[/I]I would greatly appreciate any further ideas or tips.
[LEFT][I][LEFT]

[/LEFT]
[/I][/LEFT]

---

### Post by Jake Jendiam on 2013-02-05
Same issue here. Tried installing ndiswrapper, failed. Tried compiling from source, got the kernel issue. Ran the two commands above, now stuck with:

sudo apt-get install dh-make fakeroot gcc-3.4 build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gcc-3.4
E: Couldn't find any package by regex 'gcc-3.4'

---

### Post by Jake Jendiam on 2013-02-05
I changed the gcc version to 4.7 (instead of 3.4).

Now I'm getting a different error:

/usr/src/ndiswrapper-1.57$ sudo make
make -C /usr/src/linux-headers-3.5.0-23-generic M=/usr/src/ndiswrapper-1.57
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-23-generic'
  LD      /usr/src/ndiswrapper-1.57/built-in.o
  MKEXPORT /usr/src/ndiswrapper-1.57/crt_exports.h
  MKEXPORT /usr/src/ndiswrapper-1.57/hal_exports.h
  MKEXPORT /usr/src/ndiswrapper-1.57/ndis_exports.h
  MKEXPORT /usr/src/ndiswrapper-1.57/ntoskernel_exports.h
  MKEXPORT /usr/src/ndiswrapper-1.57/ntoskernel_io_exports.h
  MKEXPORT /usr/src/ndiswrapper-1.57/rtl_exports.h
  MKEXPORT /usr/src/ndiswrapper-1.57/usb_exports.h
  MKSTUBS /usr/src/ndiswrapper-1.57/win2lin_stubs.h
  CC [M]  /usr/src/ndiswrapper-1.57/crt.o
  CC [M]  /usr/src/ndiswrapper-1.57/hal.o
  CC [M]  /usr/src/ndiswrapper-1.57/iw_ndis.o
  CC [M]  /usr/src/ndiswrapper-1.57/loader.o
  CC [M]  /usr/src/ndiswrapper-1.57/ndis.o
/usr/src/ndiswrapper-1.57/ndis.c: In function ‘NdisGetCurrentProcessorCounts’:
/usr/src/ndiswrapper-1.57/ndis.c:2657:24: error: ‘struct kernel_stat’ has no member named ‘cpustat’
/usr/src/ndiswrapper-1.57/ndis.c:2658:31: error: ‘struct kernel_stat’ has no member named ‘cpustat’
/usr/src/ndiswrapper-1.57/ndis.c:2659:17: error: ‘struct kernel_stat’ has no member named ‘cpustat’
make[2]: *** [/usr/src/ndiswrapper-1.57/ndis.o] Error 1
make[1]: *** [_module_/usr/src/ndiswrapper-1.57] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-23-generic'
make: *** [modules] Error 2

---

### Post by squakie on 2013-02-05
I'd have to look to see what you might be missing, but you're definitely having a problem with the source ndis.c not finding a "cpustat" member in a structure.  I don't know if that means you're missing a header or a library - I'd have to look at the source and see.

If someone else can't provide you with an answer let me know where you got the source and all the dependencies and I can try to find the error.  I haven't had a need for ndiswrapper for several years now.

---

### Post by squakie on 2013-02-06
I did a net search using the following search string:

ndisc.c cpustat

and it returned a lot entries - some for ubuntu, some for debian (ubuntu is based on debian) and other linux distributions.

You may want to spend some time reading those to understand what is happening and how it was solved in different situations, and then to try to apply them to your problem.

Also, I probably missed something here, but:

- if your wireless adapter is internal, post back the output of:

lspci

- if your wireless adapter is usb, post back the output of:

lsusb

Perhaps there is another way to get your adapter working.

---

### Post by Jake Jendiam on 2013-02-06
**Bus 001 Device 002: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]**
Bus 001 Device 003: ID 0480:a007 Toshiba America Info. Systems, Inc. External Disk USB 3.0
Bus 008 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I saw some other post requiring a newer version of src for ndiswrapper before making. I'll try that once I get home from work and post the details.

---

### Post by verymadpip on 2013-02-06
Probably no help, but I've had better success with the 1.58 version of Ndiswrapper:

[http://sourceforge.net/projects/ndiswrapper/files/](http://sourceforge.net/projects/ndiswrapper/files/)

---

### Post by squakie on 2013-02-06
i've taken a brief look for that adapter (bcm4323) on the net for ubuntu and just have run out of time to read much as I have an appointment to get to.

I can tell you this for using ndiswrapper, if that's the route you've chosen:

[LIST]
[*]the drivers must be Windows XP drivers (unless something has changed)
[*]the drivers must match your Ubuntu architecture - 32-bit driver for 32-bit Ubuntu, 64-bit driver for 64-bit Ubuntu.
[/LIST]


You can take a look at the net entries your self via a net search with:


ubuntu 12.10 bcm4323 driver


Don't worry if the item mentions a different brand/model adapter from yours - it's the chipset that counts:  bcm4323.

---

### Post by Jake Jendiam on 2013-02-06
> **verymadpip said:**
> Probably no help, but I've had better success with the 1.58 version of Ndiswrapper:

[http://sourceforge.net/projects/ndiswrapper/files/](http://sourceforge.net/projects/ndiswrapper/files/)

Downloaded the source (1.58, the 'test' version), then: (from here: [http://askubuntu.com/questions/132894/how-to-fix-ndiswrapper-not-found](http://askubuntu.com/questions/132894/how-to-fix-ndiswrapper-not-found))[I]sudo make uninstall sudo make
sudo make install
sudo modprobe ndiswrapper
sudo ndiswrapper -m
lsmod | grep ndiswrapper[/I]
About to reboot, I'll keep you guys posted.

---

### Post by Jake Jendiam on 2013-02-06
Posting from my wireless driver!

I already had the drivers installed from a previous attempt, instructions for that I got from here:

[http://ubuntuforums.org/showthread.php?t=1964173&highlight=NetGear+WNDA3100v2](http://ubuntuforums.org/showthread.php?t=1964173&highlight=NetGear+WNDA3100v2)

Thanks everybody!

---

### Post by verymadpip on 2013-02-07
That's great...Yay! \0/

Add ndiswrapper to /etc/modules so it'll load on boot.
I found that I had to fiddle with the module with every kernel update on 12.10, but after the first time it's not so daunting.  That didn't happen with 12.04...weird.

You could also mark the thread "solved" using the thread tools at the top of the page :)

---

