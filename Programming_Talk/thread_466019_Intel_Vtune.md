---
title: "Intel Vtune"
date: 2007-06-06
forum: Programming Talk
---

### Post by Extrudedaluminiu on 2007-06-06
Has anyone been able to get Intel Vtune running under Ubuntu? If so, could you share how?

Thanks,

---

### Post by acornett on 2007-06-30
I have been around and around with intel support about vtune on ubuntu/debian.  After lots of digging and e-mailing pages of debug info, we found the problem was in vtune detecting glibc and other libraries.  Vtune is designed to run on RedHat, and as such doesn't think it has the required dependices on debian base distros.  All of this information has been sent to Intel's engineers (I have been told) and it will hopefully be fixed in the future.

---

### Post by roio on 2009-02-15
Hi,

I currently run Intel VTune on Linux Ubuntu Server v7.10 (kernel 2.6.22) and on Linux Ubuntu "standard" v8.10. Both the linux are
for 64bit architectures.
I was in a rush so I performed the basic installation and then I added the kernel source code, the GNU compilers and the ia32-lib with apt-get. 
Eventually I installed the Intel VTune for linux. 

- Ro

---

### Post by nspattak on 2009-03-19
I am trying to install vtune 9.1 (free non commercial version) but when I try to compile vtune module for my kernel it complaints that kernel loadable module support is not enabled.

I am running 9.04 x86_64 which I update daily and these are the first lines of error:

```
Options in brackets "[ ... ]" indicate default values
that will be used when only the ENTER key is pressed.

No pre-built driver for x32_64 smp kernel 2.6.28-11-generic
was found in directory "/opt/intel/vtune/vdk" .

Proceed with building a driver for this kernel? (Yes/No) [Yes] 
C compiler to use: [ /usr/bin/gcc ] 
Make command to use: [ /usr/bin/make ] 
Kernel source directory: [ /lib/modules/2.6.28-11-generic/build ] 

checking for template makefile ... Makefile.in
checking for kernel headers ... /lib/modules/2.6.28-11-generic/build/include
checking if C compiler is working ... yes
checking if C compiler supports anonymous structs and unions ... yes
checking architecture ... x86_64
checking kernel version ... 2.6.28-11-generic
checking whether kernel modules can be built ... no

```

and

```
#======================= SOURCE CODE =============================
 
// cfgtemptest.c
 
#include <linux/autoconf.h>
#include <linux/module.h>
#include <linux/slab.h>
#include <linux/sched.h>
#include <asm/atomic.h>
int init_module(void)
{
#ifndef CONFIG_MODULES
#error "Loadable kernel module support is not enabled!"
#endif
    return 0;
}
 
#===================== COMPILER VERSION ==========================
 
/usr/bin/gcc --version
gcc (Ubuntu 4.3.3-5ubuntu4) 4.3.3
Copyright (C) 2008 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

 
#===================== COMPILER COMMAND ==========================
 
/usr/bin/gcc -D__KERNEL__ -DMODULE -DKBUILD_BASENAME="cfgtemptest" -Wall -Werror-implicit-function-declaration -Dlinux32_64 -DKERNEL_26X -fno-common -fomit-frame-pointer -fno-strict-aliasing -c cfgtemptest.c -I/lib/modules/2.6.28-11-generic/build/include -include /lib/modules/2.6.28-11-generic/build/include/linux/autoconf.h -I/lib/modules/2.6.28-11-generic/build/include/asm/mach-default
 
#====================== COMPILE ERRORS ===========================
 
In file included from /lib/modules/2.6.28-11-generic/build/include/linux/list.h:6,
                 from /lib/modules/2.6.28-11-generic/build/include/linux/module.h:9,
                 from cfgtemptest.c:2:
/lib/modules/2.6.28-11-generic/build/include/linux/prefetch.h:14:27: error: asm/processor.h: No such file or directory
/lib/modules/2.6.28-11-generic/build/include/linux/prefetch.h:15:23: error: asm/cache.h: No such file or directory
...... (output deleted)

```

Any help will be appreciated.

---

### Post by f.ficarelli on 2009-07-20
> **nspattak said:**
> I am trying to install vtune 9.1 (free non commercial version) but when I try to compile vtune module for my kernel it complaints that kernel loadable module support is not enabled.

I am running 9.04 x86_64 which I update daily and these are the first lines of error:
[...]


I faced this problem few hours ago, it showed up exactly as yours.
It seems that 2.6.28 serie (or a version greater than 2.6.24 that, according to Intel notes, is the greater one supported by VTune) lacks ${your kernel source}/include/asm/*.h links to ${kernel source}/arch/${your arch}/include/asm/*.h headers.

Be sure that:
1) the link /lib/modules/$(uname -r)/build points to your kernel sources (if you need them you can run "apt-get install linux-source-2.6.28 && cd /usr/src && tar xjf linux-source-2.6.28.tar.bz2")
2) you have built your sources at least one time to generate some needed files

After 1 and 2, you can run the following as root:

```

#!/bin/bash
set_variables()
{
  VTUNE_MOD_SRC=/opt/intel/vtune/vdk/src
  KERNEL_CUSTOM_VERSION=$(uname -r)
  KERNEL_SRC=/lib/modules/${KERNEL_CUSTOM_VERSION}/build
  KERNEL_VERSION=$(grep UTS_RELEASE ${KERNEL_SRC}/include/linux/utsrelease.h | cut -f2 -d\")
  ARCH=$(readlink ${KERNEL_SRC}/include/asm | cut -f2 -d-)
}

echo "Setting variables..."
set_variables
echo "KERNEL_CUSTOM_VERSION=${KERNEL_CUSTOM_VERSION}"
echo "KERNEL_SRC=${KERNEL_SRC}"
echo "KERNEL_VERSION=${KERNEL_VERSION}"

echo "Creating fixed include/asm link..."
cd ${KERNEL_SRC}/include
rm -f asm
ln -s ../arch/${ARCH}/include/asm asm

echo "Restoring original include/asm files..."
cp ${KERNEL_SRC}/include/asm-${ARCH}/*\.h ${KERNEL_SRC}/include/asm/

echo "Building vtune module..."
cd $VTUNE_MOD_SRC
./build-driver --kernel-version=${KERNEL_VERSION}

echo "Fixing module name..."
module=$(ls *.ko)
ln -s ${module} $(echo ${module} | sed -e "s|${KERNEL_VERSION}|${KERNEL_CUSTOM_VERSION}|")

echo "Done."

```This will rebuild the missing links.
[COLOR=Red]PLEASE NOTE THAT THE PREVIOUS CODE WILL MESS UP YOU SOURCES[/COLOR], so be sure to have a backup of the kernel source tree.
This worked like a charm for me, now running VTune.

=============================================
 Federico Ficarelli
 CINECA - High Performance Computing Group
          Bologna - Italy

---

### Post by fasiha on 2009-10-14
> **f.ficarelli said:**
> I faced this problem few hours ago, it showed up exactly as yours.

echo "Fixing module name..."
module=$(ls *.ko)
ln -s ${module} $(echo ${module} | sed -e "s|${KERNEL_VERSION}|${KERNEL_CUSTOM_VERSION}|")

echo "Done."

It doesn't work for me fully. Please explain the above mentioned module setting with an example. I have to configure it all for fedora platform so i need to understand this thing fully so that i can set it in my platform compatible way.

---

### Post by monster on 2009-10-19
Thank you very much Federico.
I, and probably others appreciate your shortcut very much.
This script is working perfectly for Ubuntu 9.04

What problems do you have with Fedora now?

---

### Post by squid_052 on 2009-10-19
> **f.ficarelli said:**
> This will rebuild the missing links.
[COLOR=Red]PLEASE NOTE THAT THE PREVIOUS CODE WILL MESS UP YOU SOURCES[/COLOR], so be sure to have a backup of the kernel source tree.
This worked like a charm for me, now running VTune.



What's the best way to backup the kernel source tree, and also to restore?

Just in case :P
Thanks

---

### Post by monster on 2009-10-23
You can copy /usr/src/linux-source-[your version] to the safe place.
But actually this directory is in the repository if you have standard kernel so no worry about overwriting your sources.

---

