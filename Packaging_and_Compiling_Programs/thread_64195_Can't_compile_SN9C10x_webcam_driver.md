---
title: "Can't compile SN9C10x webcam driver"
date: 2005-09-10
forum: Packaging and Compiling Programs
---

### Post by jdawdy on 2005-09-10
I have a Genius videocam NB 300 webcam, which apparently requires a slightly edited SN9C10x driver.  Instructions at [http://www.linux-projects.org/modules/newbb/viewtopic.php?topic_id=167&forum=3](http://www.linux-projects.org/modules/newbb/viewtopic.php?topic_id=167&forum=3)

I downloaded and unzipped the driver, installed build-essentials and the current i386 kernal source package. I added a build folder to /lib/modules/2.6.10-5-386 as that was the initial error * no directory found*.  

Now when I try make modules I get

jim@Jim:~$ cd sn9c102-1.24
jim@Jim:~/sn9c102-1.24$ sudo make modules
Password:
**************************************************************************
* Building Video4Linux2 driver v1.24 for SN9C10x PC Camera Controllers...*
* Official Linux 2.6.10 is the minimum version for this driver.          *
* Read the documentation "sn9c102.txt" for more informations.            *
* Type "make help" for a list of available targets.                      *
**************************************************************************

make -C /lib/modules/2.6.10-5-386/build M=/home/jim/sn9c102-1.24 modules
make[1]: Entering directory `/lib/modules/2.6.10-5-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.10-5-386/build'
make: *** [modules] Error 2


The instructions from the .txt file are (though I am not sure how to determine if the kernel configuration files has these options enabled):

The following options of the kernel configuration file must be enabled and
corresponding modules must be compiled:

	# Multimedia devices
	#
	CONFIG_VIDEO_DEV=m

	# USB support
	#
	CONFIG_USB=m

In addition, depending on the hardware being used, the modules below are
necessary:

	# USB Host Controller Drivers
	#
	CONFIG_USB_EHCI_HCD=m
	CONFIG_USB_UHCI_HCD=m
	CONFIG_USB_OHCI_HCD=m

Moving along to the SN9C10x driver: after having downloaded the package,
decompress and compile:

	[user@localhost home]$ tar xvzf sn9c102-x.x.tar.gz
	[user@localhost home]$ cd sn9c102-x.x

(where "x.x" has to be substituted with the right version of the module just
downloaded)

It is necessary to properly configure your particular kernel source tree before
compiling the driver. The modular building process is used; therefore you must
have read and write access to your kernel source tree. If not, log in as root
before running the following commands:

	[user@localhost sn9c102-x.x]$ make clean
	[user@localhost sn9c102-x.x]$ make modules

If the commands fail, control the Makefile and change the path to the kernel
source tree or to any other files, according to your system configuration;
then run the previous commands again.

Please help!

Jim

---

### Post by jdawdy on 2005-09-10
Ok, I think I see what I was doing wrong.  The driver is already included in the linux source, however a small change has to be made to the code and the kernel recompiled (I think).

So I downloaded the linux-source and followed the steps in the Kernal recompile howto.  When I try
sudo make-kpkg --append-to-version=-custom kernel_image modules_image it works fine up until:

make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
echo done >  stamp-kernel-configure
echo done >  stamp-configure
if [ -f include/linux/version.h ]; then  \
             uts_ver=$(grep 'define UTS_RELEASE' include/linux/version.h | perl -nle  'm/^\s*\#define\s+UTS_RELEASE\s+("?)(\S+)\1/g && print $2;'); \
    if [ "X$uts_ver" != "X2.6.10-custom" ]; then              \
                echo "The UTS Release version in include/linux/version.h";           \
        echo "     \"$uts_ver\" ";  \
                echo "does not match current version " ;           \
                echo "     \"2.6.10-custom\" " ;     \
                echo "Reconfiguring." ;           \
                touch Makefile;           \
             fi;           \
fi
test -f stamp-configure || /usr/bin/make -f /usr/share/kernel-package/rules configure
/usr/bin/make  EXTRAVERSION=-custom  ARCH=i386 \
                     bzImage
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
  CHK     include/linux/version.h
make[2]: *** No rule to make target `init/main.o', needed by `init/built-in.o'.  Stop.
make[1]: *** [init] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make: *** [stamp-build] Error 2
root@Jim:/usr/src/linux #

Thanks
Jim

---

### Post by jdawdy on 2005-09-10
Ok, I think I see what I was doing wrong.  The driver is already included in the linux source, however a small change has to be made to the code and the kernel recompiled (I think).

So I downloaded the linux-source and followed the steps in the Kernal recompile howto.  When I try
sudo make-kpkg --append-to-version=-custom kernel_image modules_image it works fine up until:

make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
echo done >  stamp-kernel-configure
echo done >  stamp-configure
if [ -f include/linux/version.h ]; then  \
             uts_ver=$(grep 'define UTS_RELEASE' include/linux/version.h | perl -nle  'm/^\s*\#define\s+UTS_RELEASE\s+("?)(\S+)\1/g && print $2;'); \
    if [ "X$uts_ver" != "X2.6.10-custom" ]; then              \
                echo "The UTS Release version in include/linux/version.h";           \
        echo "     \"$uts_ver\" ";  \
                echo "does not match current version " ;           \
                echo "     \"2.6.10-custom\" " ;     \
                echo "Reconfiguring." ;           \
                touch Makefile;           \
             fi;           \
fi
test -f stamp-configure || /usr/bin/make -f /usr/share/kernel-package/rules configure
/usr/bin/make  EXTRAVERSION=-custom  ARCH=i386 \
                     bzImage
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
  CHK     include/linux/version.h
make[2]: *** No rule to make target `init/main.o', needed by `init/built-in.o'.  Stop.
make[1]: *** [init] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make: *** [stamp-build] Error 2
root@Jim:/usr/src/linux #

I can't figure out why Im getting this error.

Thanks
Jim

---

