---
title: "Cannot compile kernel using KernelCompile Community Documentation"
date: 2012-02-14
forum: Packaging and Compiling Programs
---

### Post by DarthHack on 2012-02-14
OS: Ubuntu 11.10
Kernel: 3.0.0-15-generic-pae


After reading the instructions here's the list of commands that I have used to get where I am:


cd ~/src
sudo apt-get install fakeroot build-essential crash kexec-tools makedumpfile kernel-wedge
sudo apt-get build-dep linux
sudo apt-get install git-core libncurses5 libncurses5-dev libelf-dev asciidoc binutils-dev
sudo apt-get build-dep --no-install-recommends linux-image-$(uname -r)
apt-get source linux-image-$(uname -r)
cd linux-3.0.0
cp /boot/config-3.0.0-15-generic-pae .config
chmod -R u+x debian/scripts/*
debian/rules updateconfigs
fakeroot debian/rules clean
DEB_BUILD_OPTIONS=parallel=2 AUTOBUILD=1 NOEXTRAS=1 fakeroot debian/rules binary-debs


Here's the error:


make ARCH=i386 CROSS_COMPILE= KERNELVERSION=3.0.0-15-generic CONFIG_DEBUG_SECTION_MISMATCH=y KBUILD_BUILD_VERSION="26" LOCALVERSION= localver-extra= O=/home/matt/src/linux-3.0.0/debian/build/build-generic -j1 silentoldconfig prepare scripts
make[1]: Entering directory `/home/matt/src/linux-3.0.0'
make[3]: Nothing to be done for `/home/matt/src/linux-3.0.0/Makefile'.
  GEN     /home/matt/src/linux-3.0.0/debian/build/build-generic/Makefile
scripts/kconfig/conf --silentoldconfig Kconfig
.config:5165:warning: override: TREE_RCU changes choice state
.config:6049:warning: override: MACH_NO_WESTBRIDGE changes choice state
#
# configuration written to .config
#
  Using /home/matt/src/linux-3.0.0 as source for kernel
  /home/matt/src/linux-3.0.0 is not clean, please run 'make mrproper'
  in the '/home/matt/src/linux-3.0.0' directory.
make[4]: *** [prepare3] Error 1
make[3]: *** [sub-make] Error 2
make[2]: *** [prepare] Error 2
make[1]: *** [sub-make] Error 2
make[1]: Leaving directory `/home/matt/src/linux-3.0.0'
make: *** [/home/matt/src/linux-3.0.0/debian/stamps/stamp-prepare-tree-generic] Error 2


Can someone point me to the step that I missed, the extra step that I put in, the wrong order, the misspelling!  From my point of view I gave the darned thing a .config file, why does it want to go an change settings automagically?!?

At this point I am very frustrated.  I started this whole process to learn how to build kernel modules by compiling a 10 line kernel module.  Four hours later and I haven't learned anything useful.  Once upon a time kernel building didn't seem to be so hard.  If I just run "make oldconfig && make" in the kernel source folder it will chug for hours and produce a vmlinux binary, but it is huge when compared to the kernel in /boot.  Maybe it gets stripped or compressed when the package is built, but I worry that it isn't what I want.

BTW, I also tried binary-generic-pae, since I noticed that it says that it is building the generic kernel not the generic-pae kernel, but this didn't change anything.

---

### Post by SevenMachines on 2012-02-14
> At this point I am very frustrated.  I started this whole process to learn how to build kernel modules by compiling a 10 line kernel module.  Four hours later and I haven't learned anything useful.
Can I just check, are you actually wanting to build a custom kernel? Because it sounds like you want to build kernel modules which is a very different thing. For kernel modules you need 

* The kernel headers, ie one of the linux-headers- packages, most probably
$ sudo apt-get install linux-headers-`uname -r`

* some c files with your module code

* A simple makefile

Look at [http://tldp.org/LDP/lkmpg/2.6/html/](http://tldp.org/LDP/lkmpg/2.6/html/), try out the hello world module in section 2.1 with the makefile in 2.2

---

### Post by DarthHack on 2012-02-14
Thank you for the reply!

sudo apt-get install linux-headers-`uname -r`

creates the build link in the /lib/modules/$(uname -r) folder that was missing and was the reason why I downloaded the kernel in the first place as the kernel source also provides all of these goodies.

You seem to have been around the block a few times with Debian/Ubuntu, so please don't think I am being ungrateful, but I have to ask a couple more questions in the hope that you can give me another tasty nugget.

Cynically, I wonder if you have any idea what is wrong with the instructions for building a kernel at:

[http://help.ubuntu.com/community/Kernel/Compile](http://help.ubuntu.com/community/Kernel/Compile)

They do not seem to work in any way shape or form even though they seem to have been last updated only a month ago.  Seems like they either need some serious clarification or they need to be removed.

Pragmatically, I wonder if you know the set of commands that the Ubuntu team uses to compile its official kernels or a reference that explains the steps that the Debian/Ubuntu kernel build scripts are taking, so that I can understand how to control the build, not just have a copy and paste set of commands.  It has been 10+ years since I last built a kernel on Slackware, I have a general knowledge of the fundamentals, but Linux has grown a bit and its build practices have also grown.

Seriously, drop me a message and let me know where I can send your pizza.  You have saved me a lot of time (maybe some hair too).

---

### Post by SevenMachines on 2012-02-15
Hi there. The set of commands you used would work, with one alteration. Don't copy the config from /boot to .config. That'll probably be where
```
   /home/matt/src/linux-3.0.0 is not clean, please run 'make mrproper'
```comes from. Meaning the source tree is not pristine, kernel packages seem strict about this.
The method you're using is to use the exact same packages as ubuntu as using, then maybe tweak some config elements or perhaps even add a patch or two, then create the same set of kernel packages as ubuntu does. To alter config options, look in  debian/config/ARCH/ and edit away, this will change what options are used to build that package, these are whats passed as .config in the fake build environment during th package build

In general there are 2 main occasions where I find myself wanting to build a kernel
* The method you used, to build a tweaked config kernel for enabling some option or other ubuntu has disabled. This is handy in that creates packages that are exactly the same as ubuntus but just with minor tweaks
* Pulling from git for the latest and greatest kernel.
Note you can make menuconfig to this day with kernel source, the commands you were using though are to build *packages* remember, you could still build and install the kernels manually if you wanted

---

### Post by DarthHack on 2012-02-19
As my final entry for this thread, I would suggest that anyone who is interested in building a Ubuntu kernel not use the KernelCompile document at:

[http://help.ubuntu.com/community/Kernel/Compile](http://help.ubuntu.com/community/Kernel/Compile)

But instead use the Ubuntu Kernel Team's KernelMaintenance page at:

[http://wiki.ubuntu.com/KernelTeam/KernelMaintenance](http://wiki.ubuntu.com/KernelTeam/KernelMaintenance)

The "Performing Builds" section is especially helpful, but overall the KernelMaintenance document is MUCH better organized and gives better insight into the logic behind Ubuntu kernel builds.  Keep in mind though, that much of the KernelMaintenance document deals with procedures for updating the Ubuntu kernel repository, so some sections are definitely useful only for the Ubuntu Kernel Team.

Thanks again SevenMachines.

---

