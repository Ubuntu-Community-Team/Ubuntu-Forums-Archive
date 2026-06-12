---
title: "Compiling webcam drivers"
date: 2005-01-31
forum: Packaging and Compiling Programs
---

### Post by Yukino on 2005-01-31
Hi

It's the first time I try to compile something like drivers... and I have a problem.
I've downloaded the drivers for Logitech Quickcam Messenger and when I do "make all", I get

```
 $ make all
make -C "/lib/modules/2.6.8.1-3-386/build" SUBDIRS="/home/rosa/qc-usb-messenger-0.8" modules V=1 USER_OPT=""
make[1]: Entering directory `/usr/src/linux-2.6.8.1'
Makefile:415: .config: No such file or directory
mkdir -p /home/rosa/qc-usb-messenger-0.8/.tmp_versions
make -f scripts/Makefile.build obj=/home/rosa/qc-usb-messenger-0.8
  Building modules, stage 2.
make -rR -f /usr/src/linux-2.6.8.1/scripts/Makefile.modpost
  scripts/mod/modpost -i /usr/src/linux-2.6.8.1/Module.symvers /home/rosa/qc-usb-messenger-0.8/quickcam.o
/bin/sh: line 1: scripts/mod/modpost: No such file or directory
make[2]: *** [__modpost] Error 127
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.8.1'
make: *** [quickcam.ko] Error 2

```

I try to "make modpost " (I don't know if this is possible) in scripts/mod, but it seems that I need the file "elfconfig.h".

I have the kernel source files in /usr/src/linux-2.6.8.1 and I made a symbolic link from  /lib/modules/"my kernel"/build. Is this correct?
Any idea?

---

### Post by isaac on 2005-02-06
i have this kind of problem too ..

I'm using logitech webcam express (Vendor ID 920)
download a driver spca532-23-062004 from [http://qce-ga.sourceforge.net/](http://qce-ga.sourceforge.net/)
this driver work in Redhat Linux 9 but i get the same problem as yours compiling it in ubuntu... someone pls help us... thanks in advance

---

### Post by kleeman on 2005-02-06
There appear to be special Ubuntu packages for qce-ga e.g.
[http://cpan.cybercomm.nl/pub2/ubuntu/pool/universe/q/qce-ga/](http://cpan.cybercomm.nl/pub2/ubuntu/pool/universe/q/qce-ga/)
these come from Debian unstable. I suggest installing these packages and trying to find instructions for making the kernel modules within the packages. Often the make process you are trying depends sensitively on details within the source tree i.e. on the distro it is designed for....

---

### Post by cheleb on 2005-02-06
Hi Yukino,

do you have the matching kernel-headers package for your kernel installed?
There's a script in the toplevel directory of your driver source called "quickcam.sh".
Execute this and it will guide you through the build/installation process and will warn you if something is missing on your machine.

Cheers.
cheleb

---

### Post by soulsniper on 2005-06-03
I have the QuickCam Messenger and have successfully installed using those drivers. Easiest way to install it is to do the following:

[list]
[*]Make sure **build-essential** and the correct **linux-headers** package is installed. Use synaptic for this, or ```
apt-get install build-essential
apt-get install linux-headers-386
```
[*]Make sure XawTV is installed. This is not **strictly** necessary, but helps with testing. Use synaptic for this, or ```
apt-get install xawtv
``` 
[*]Download the latest qc-usb-messenger file from [here](http://home.mag.cx/messenger/source/qc-usb-messenger-0.8.tar.gz) 
[*]Extract all files using ```
tar xvzf qc-usb-messenger-0.8.tar.gz
```
[*]Change to the directory created: ```
cd qc-usb-messenger-0.8
```
[*]Run the setup-wizard included: ```
./quickcam.sh
```
[*]Follow all the on-screen instructions. At one point, the setup wizard may say "No Compatible Cameras found", ignore this and continue anyway. I'm not sure why this happens but everything seemed to work fine for me anyway! You may have to enter your root password during the process.
[/list] 

You will know if it is successful or not because the setup wizard will run XawTV and show you a live webcam feed (as long as you have XawTV installed!)

I have installed this fine on Hoary a few days ago, so it should work  :)

---

