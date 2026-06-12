---
title: "Logitech webcam headache"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by mattjack66 on 2008-08-16
Hi,
I have logitech quickcam 5.0.1 and i downloaded the drivers but i am having having problems.
when i type make all in the driver directory (from [http://qce-ga.sourceforge.net/](http://qce-ga.sourceforge.net/)), here's what i get: 

make -C "/lib/modules/2.6.24-19-generic/build" SUBDIRS="/home/matt/Desktop/qc-usb-0.6.6" modules V=1 USER_OPT="-DHAVE_UTSRELEASE_H=1"
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /home/matt/Desktop/qc-usb-0.6.6/.tmp_versions ; rm -f /home/matt/Desktop/qc-usb-0.6.6/.tmp_versions/*
make -f scripts/Makefile.build obj=/home/matt/Desktop/qc-usb-0.6.6
  gcc -m32 -Wp,-MD,/home/matt/Desktop/qc-usb-0.6.6/.qc-driver.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -DNOKERNEL -DHAVE_UTSRELEASE_H=1  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc_driver)"  -D"KBUILD_MODNAME=KBUILD_STR(quickcam)" -c -o /home/matt/Desktop/qc-usb-0.6.6/.tmp_qc-driver.o /home/matt/Desktop/qc-usb-0.6.6/qc-driver.c
In file included from /home/matt/Desktop/qc-usb-0.6.6/qc-driver.c:47:
/home/matt/Desktop/qc-usb-0.6.6/quickcam.h:129:1: warning: "BIT" redefined
In file included from include/linux/kernel.h:15,
                 from include/linux/cache.h:4,
                 from include/linux/time.h:7,
                 from include/linux/videodev2.h:59,
                 from include/linux/videodev.h:15,
                 from /home/matt/Desktop/qc-usb-0.6.6/quickcam.h:95,
                 from /home/matt/Desktop/qc-usb-0.6.6/qc-driver.c:47:
include/linux/bitops.h:6:1: warning: this is the location of the previous definition
/home/matt/Desktop/qc-usb-0.6.6/qc-driver.c: In function ‘qc_i2c_init’:
/home/matt/Desktop/qc-usb-0.6.6/qc-driver.c:824: error: ‘struct urb’ has no member named ‘lock’
/home/matt/Desktop/qc-usb-0.6.6/qc-driver.c:825: warning: assignment from incompatible pointer type
/home/matt/Desktop/qc-usb-0.6.6/qc-driver.c: In function ‘qc_isoc_start’:
/home/matt/Desktop/qc-usb-0.6.6/qc-driver.c:1867: warning: assignment from incompatible pointer type
/home/matt/Desktop/qc-usb-0.6.6/qc-driver.c: At top level:
/home/matt/Desktop/qc-usb-0.6.6/qc-driver.c:3009: error: unknown field ‘hardware’ specified in initializer
make[2]: *** [/home/matt/Desktop/qc-usb-0.6.6/qc-driver.o] Error 1
make[1]: *** [_module_/home/matt/Desktop/qc-usb-0.6.6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [quickcam.ko] Error 2

I have build-essentials installed just so you know...

any help is appreciated!
THANKS!!!!!

---

### Post by y-lee on 2008-08-18
Do you have linux-headers-`uname -r` installed?

---

### Post by ibuclaw on 2008-08-18
The source code is availiable from the repository.
Although, the current version in Hardy appears to be the same, and gives the same erroneous output you get.

The Intrepid Version, however builds just fine for me.

First run this
```
sudo apt-get install bzip2 deb-helper kernel-package make module-assistant linux-headers-$(uname -r)
```

and download the deb package from [here]("http://mirrors.kernel.org/ubuntu/pool/universe/q/qc-usb/qc-usb-source_0.6.6-5_all.deb").

Instead of installing it, save it to your Desktop and extract it's contents.
```
cd ~/Desktop
dpkg -x qc-usb-source_0.6.6-5_all.deb qc-usb-source
cd qc-usb-source/usr/src
tar -jxf qc-usb.tar.bz2
cd modules/qc-usb

```
And then to build/install run
```
make && sudo make install
```
Then to load the modules, it should be:
```
sudo modprobe videodev
sudo modprobe usb-uhci
sudo modprobe usb-ohci
sudo modprobe quickcam

```
And, hopefully, the driver will work (test it in an app such as **cheese**).

If not, may I point your attention at a util for the webcam in the repo too.
```
sudo apt-get install qc-usb-utils
```
And the command file in that is call **qcset**, play about with it and see what it does.

Regards
Iain

---

### Post by mattjack66 on 2008-08-19
> **y-lee said:**
> Do you have linux-headers-`uname -r` installed?

no. Thanks!

---

### Post by mattjack66 on 2008-08-19
> **tinivole said:**
> The source code is availiable from the repository.
Although, the current version in Hardy appears to be the same, and gives the same erroneous output you get.

The Intrepid Version, however builds just fine for me.

First run this
```
sudo apt-get install bzip2 deb-helper kernel-package make module-assistant linux-headers-$(uname -r)
```

and download the deb package from [here]("http://mirrors.kernel.org/ubuntu/pool/universe/q/qc-usb/qc-usb-source_0.6.6-5_all.deb").

Instead of installing it, save it to your Desktop and extract it's contents.
```
cd ~/Desktop
dpkg -x qc-usb-source_0.6.6-5_all.deb qc-usb-source
cd qc-usb-source/usr/src
tar -jxf qc-usb.tar.bz2
cd modules/qc-usb

```
And then to build/install run
```
make && sudo make install
```
Then to load the modules, it should be:
```
sudo modprobe videodev
sudo modprobe usb-uhci
sudo modprobe usb-ohci
sudo modprobe quickcam

```
And, hopefully, the driver will work (test it in an app such as **cheese**).

If not, may I point your attention at a util for the webcam in the repo too.
```
sudo apt-get install qc-usb-utils
```
And the command file in that is call **qcset**, play about with it and see what it does.

Regards
Iain

heres what i get...  besides a bunch of errors
matt@matts-desktop:~/Desktop/qc-usb-source/usr/src/modules/qc-usb$ sudo modprobe videodev
matt@matts-desktop:~/Desktop/qc-usb-source/usr/src/modules/qc-usb$ sudo modprobe usb-uhci
FATAL: Module usb_uhci not found.
matt@matts-desktop:~/Desktop/qc-usb-source/usr/src/modules/qc-usb$ sudo modprobe usb-ohci
FATAL: Module usb_ohci not found.
matt@matts-desktop:~/Desktop/qc-usb-source/usr/src/modules/qc-usb$ sudo modprobe quickcam

didnt work... :(

---

### Post by mattjack66 on 2008-08-19
latest update..
 
```
matt@matts-desktop:~/Desktop/qc-usb-0.6.6$ ./quickcam.sh LINUX_DIR=/usr/src/linux-source-2.6.24
-=- Logitech QuickCam USB camera driver installer -=-
Hello! I am the (hopefully) easy-to-use, fully automated
qc-usb driver installation script.
At the moment, this is experimental, and if it doesn't work,
don't hesitate to quit this with Ctrl+C and install the
driver manually.

The driver is provided in source code form, so it has to be
compiled. This should happen automatically, but it does mean
that there are some steps required before installation.

You also need to know "root" user password to test and
install the driver.

Basically you need only to keep hitting Enter whenever you
see this prompt: --->. Sometimes you're asked root password.
Pay special attention to lines beginning with [!].
It means that some trouble has been detected.

To most important location is the path to your kernel source
or headers. This can be guessed, but you can specify it by
giving it as an argument to this script like this:
	./quickcam.sh LINUX_DIR=/usr/src/linux

If you haven't done it yet, now it would be a good moment to
take a look at file README.
Argument found: LINUX_DIR=/usr/src/linux-source-2.6.24

Next I'm going to check if you have some important programs installed
and if they and the kernel are of suitable version.
Press Ctrl+C to quit, Enter to continue ---> 

./quickcam.sh
/usr/bin/whoami
/bin/su
/bin/ls
/bin/cat
/usr/bin/gcc
/usr/bin/gcc
/usr/bin/make
/bin/grep
/bin/egrep
/usr/bin/awk
/bin/sed
/usr/bin/tail
/usr/bin/head
/usr/bin/install
/usr/bin/ld
/bin/uname
/usr/bin/tr
/usr/bin/xawtv
/usr/bin/xdpyinfo
/bin/dmesg
/usr/bin/wc
/bin/readlink
gcc version: gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
gcc version: gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Make version: GNU Make 3.81
Linker version: GNU ld (GNU Binutils for Ubuntu) 2.18.0.20080103
Kernel compiler: gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Looking for more necessary programs...
Found program /sbin/depmod
Found program /sbin/insmod
Found program /sbin/rmmod
Found program /sbin/modprobe
Found program /bin/mount
Found program /usr/sbin/lsusb
depmod version: module-init-tools 3.3-pre11
insmod version: module-init-tools version 3.3-pre11
rmmod version: module-init-tools version 3.3-pre11
modprobe version: module-init-tools version 3.3-pre11
Checking whether we're root... matt
Checking for driver source code...
Checking for write permission...

Previous round done. Now checking if you have kernel source installed.
Press Ctrl+C to quit, Enter to continue ---> 

awk: cannot open /usr/src/linux-source-2.6.24/include/linux/version.h (No such file or directory)
[: 1: 132608: unexpected operator
[: 1: 132608: unexpected operator
Kernel source directory: /usr/src/linux-source-2.6.24
Detected kernel version is 2.6.x.
[!] Kernel configuration file /usr/src/linux-source-2.6.24/.config not found.
If the headers have been already configured properly, you might
not need it. But it would be better not to trust this, you
really should know where is your configuration file, and
copy it into its place. Often it can be found in /boot/
directory with a name like /boot/config-2.4.26 or something.
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue --->
```

---

### Post by chkneater on 2008-08-19
I used an apt named Camorama to get my QuickCam to work.  It's an older QuickCam and it still worked with Ubuntu 8.04.  Can't remember where I got the app but search it and try.

---

### Post by mattjack66 on 2008-08-19
oh. now it works... thank you! 
I wonder if that app had special drivers...
but i would still like to know how to get it to work regularly

---

### Post by ibuclaw on 2008-08-20
> **mattjack66 said:**
> heres what i get...  besides a bunch of errors
matt@matts-desktop:~/Desktop/qc-usb-source/usr/src/modules/qc-usb$ sudo modprobe videodev
matt@matts-desktop:~/Desktop/qc-usb-source/usr/src/modules/qc-usb$ sudo modprobe usb-uhci
FATAL: Module usb_uhci not found.
matt@matts-desktop:~/Desktop/qc-usb-source/usr/src/modules/qc-usb$ sudo modprobe usb-ohci
FATAL: Module usb_ohci not found.
matt@matts-desktop:~/Desktop/qc-usb-source/usr/src/modules/qc-usb$ sudo modprobe quickcam

didnt work... :(

Are you sure?

You could have quite easily confused a successful install with errors.
Makefiles will produce alot of output, but those aren't necessarily erroneous.

also, did you get the "FATAL" message when you ran "sudo modprobe quickcam" ?
> 
matt@matts-desktop:~/Desktop/qc-usb-source/usr/src/modules/qc-usb$ sudo modprobe videodev
matt@matts-desktop:~/Desktop/qc-usb-source/usr/src/modules/qc-usb$ sudo modprobe quickcam

That little snip tells me that you were successful in making and installing the drivers for your webcam, and that they were successfully loaded onto your computer. You just needed the right software to interact with it.

Regards
Iain

---

### Post by mattjack66 on 2008-08-20
> **tinivole said:**
> Are you sure?

You could have quite easily confused a successful install with errors.
Makefiles will produce alot of output, but those aren't necessarily erroneous.

also, did you get the "FATAL" message when you ran "sudo modprobe quickcam" ?

That little snip tells me that you were successful in making and installing the drivers for your webcam, and that they were successfully loaded onto your computer. You just needed the right software to interact with it.

Regards
Iain

thanks! but i was trying to get it to work with skype... and the screen was blank. now when i use camorama or xawtv it works perfectly. ugh, who invented drivers?

---

### Post by m1chaelf on 2008-09-12
> **mattjack66 said:**
> The source code is availiable from the repository.
Although, the current version in Hardy appears to be the same, and gives the same erroneous output you get.

The Intrepid Version, however builds just fine for me.

First run this
Code:

sudo apt-get install bzip2 deb-helper kernel-package make module-assistant linux-headers-$(uname -r)

and download the deb package from here.

Instead of installing it, save it to your Desktop and extract it's contents.
Code:

cd ~/Desktop
dpkg -x qc-usb-source_0.6.6-5_all.deb qc-usb-source
cd qc-usb-source/usr/src
tar -jxf qc-usb.tar.bz2
cd modules/qc-usb

And then to build/install run
Code:

make && sudo make install

Then to load the modules, it should be:
Code:

sudo modprobe videodev
sudo modprobe usb-uhci
sudo modprobe usb-ohci
sudo modprobe quickcam

And, hopefully, the driver will work (test it in an app such as cheese).

If not, may I point your attention at a util for the webcam in the repo too.
Code:

sudo apt-get install qc-usb-utils

And the command file in that is call qcset, play about with it and see what it does.

Regards
Iain
when I run the code:
sudo apt-get install bzip2 deb-helper kernel-package make module-assistant linux-headers-$(uname -r)
deb_helper cannot be found. I'm a noob

If I drop the call for deb_helper out of that line and continue on, the line to compile will give me more errors than the terminal can display.

---

