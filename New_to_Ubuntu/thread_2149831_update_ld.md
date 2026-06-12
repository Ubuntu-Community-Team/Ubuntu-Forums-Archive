---
title: "update ld"
date: 2013-05-30
forum: New to Ubuntu
---

### Post by adityaharish on 2013-05-30
I'm trying to install glibc from source code. I'm  getting some when I try to configure glib

Code :
[B]shraddesh@shraddesh-Samsung-Desktop-System:~/Downloads/glibc-build$ ./glibc-2.17/configure --prefix=/usr
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... /usr/bin/gcc
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether /usr/bin/gcc accepts -g... yes
checking for /usr/bin/gcc option to accept ISO C89... none needed
checking how to run the C preprocessor... /usr/bin/gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for readelf... readelf
checking for sysdeps preconfigure fragments... x86_64 
configure: running configure fragment for add-on libidn
configure: running configure fragment for add-on nptl
checking add-on ports for preconfigure fragments... aarch64 alpha am33 arm hppa ia64 m68k mips tile 
checking for assembler and linker STT_GNU_IFUNC support... yes
checking whether .text pseudo-op must be used... yes
checking sysdep dirs... nptl/sysdeps/unix/sysv/linux/i386/i686 sysdeps/unix/sysv/linux/i386/i686 nptl/sysdeps/unix/sysv/linux/i386 nptl/sysdeps/unix/sysv/linux/x86 sysdeps/unix/sysv/linux/x86 sysdeps/unix/sysv/linux/i386/nptl sysdeps/unix/sysv/linux/i386 nptl/sysdeps/unix/sysv/linux nptl/sysdeps/pthread sysdeps/pthread ports/sysdeps/unix/sysv/linux sysdeps/unix/sysv/linux sysdeps/gnu sysdeps/unix/inet nptl/sysdeps/unix/sysv ports/sysdeps/unix/sysv sysdeps/unix/sysv sysdeps/unix/i386 nptl/sysdeps/unix ports/sysdeps/unix sysdeps/unix sysdeps/posix sysdeps/i386/i686/fpu/multiarch sysdeps/i386/i686/fpu sysdeps/i386/i686/multiarch nptl/sysdeps/i386/i686 sysdeps/i386/i686 sysdeps/i386/i486 nptl/sysdeps/i386/i486 sysdeps/i386/fpu sysdeps/x86/fpu nptl/sysdeps/i386 sysdeps/i386 sysdeps/x86 sysdeps/wordsize-32 sysdeps/ieee754/ldbl-96 sysdeps/ieee754/dbl-64 sysdeps/ieee754/flt-32 sysdeps/ieee754 sysdeps/generic
configure: WARNING: add-on ports contributed no useful sysdeps directories
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether as is GNU as... yes
checking whether ld is GNU ld... yes
checking for as... as
checking version of as... 2.22, ok
checking for ld... ld
checking version of ld... v. ?.??, bad
checking for gcc... /usr/bin/gcc
checking version of /usr/bin/gcc... 4.6.4, ok
checking for gnumake... no
checking for gmake... no
checking for make... make
checking version of make... 3.81, ok
checking for gnumsgfmt... no
checking for gmsgfmt... no
checking for msgfmt... msgfmt
checking version of msgfmt... 0.18.1, ok
checking for makeinfo... makeinfo
checking version of makeinfo... 4.13, ok
checking for sed... sed
checking version of sed... 4.2.1, ok
checking for gawk... gawk
checking version of gawk... 3.1.8, ok
checking for nm... nm
checking for autoconf... autoconf
checking whether autoconf works... no
configure: error: 
*** These critical programs are missing or too old: ld
*** Check the INSTALL file for required versions.
shraddesh@shraddesh-Samsung-Desktop-System:~/Downloads/glibc-build$ 


[/B]
So Please tell me how to update ld ???

---

### Post by lethall1 on 2013-05-30
>  [B]checking whether autoconf works... no
configure: error: 
*** These critical programs are missing or too old: ld[/B]
did you try to install it?
Here is no information about your dist, but why dont you use "apt-get build-dep glibc-devel"?
[http://www.linuxquestions.org/questions/linux-from-scratch-13/'program-too-old'-error-when-installing-glibc-2-9-a-768992/](http://www.linuxquestions.org/questions/linux-from-scratch-13/'program-too-old'-error-when-installing-glibc-2-9-a-768992/)

---

### Post by adityaharish on 2013-05-30
I'm on ubuntu 12.04. I tried installing binutils but it's breaking the linker path gcc needs .

Code:[B]
shraddesh@shraddesh-Samsung-Desktop-System:~/Downloads/glibc-build$ uname -a
Linux shraddesh-Samsung-Desktop-System 3.2.0-44-generic-pae #69-Ubuntu SMP Thu May 16 18:50:07 UTC 2013 i686 i686 i386 GNU/Linux
shraddesh@shraddesh-Samsung-Desktop-System:~/Downloads/glibc-build$ sudo apt-get build-dep glibc-devel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for glibc-devel
shraddesh@shraddesh-Samsung-Desktop-System:~/Downloads/glibc-build$ 
[/B]

---

### Post by lethall1 on 2013-05-30
as i remember, you must install build-essentials, which depends on glibc.

---

### Post by adityaharish on 2013-05-30
I have already done that .. still the same error crops up .

---

### Post by adityaharish on 2013-05-31
Can anyone please tell me how to upgrade ld to higher version ??
I'm working on WebKit which requires glibc which in turn requires a higher version of ld. Mine is 1.11
It requires at least 1.53 . 
So please tell me how to proceed.
If I try to install binutils from source code like binutils-2.23  it upgrades ld to a higher version but then I get this error when I compile a .c file

Code:

[B]shraddesh@shraddesh-Samsung-Desktop-System:~$ vi test.c shraddesh@shraddesh-Samsung-Desktop-System:~$ gcc test.c /usr/bin/ld: this linker was not configured to use sysroots collect2: error: ld returned 1 exit status shraddesh@shraddesh-Samsung-Desktop-System:~$

[/B]Please help me asap.I'm in dire need of WebKit tool now..

Thanks & Regards,
Aditya

---

### Post by mörgæs on 2013-05-31
If you want the latest version of ld and glibc (and their dependencies) wouldn't it be better to begin with a fresh install of 13.04?

---

### Post by adityaharish on 2013-05-31
I don't have enough resources to upgrade to 13.04 i.e I don't have the installation disk nor pen drive.
Moreover the our network of pc's are blocked of transferring data through external disks.

So don't I have any solution to upgrade ld in the current version of Ubuntu (12.04 ) ??

---

