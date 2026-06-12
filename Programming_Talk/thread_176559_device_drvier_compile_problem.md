---
title: "device drvier compile problem"
date: 2006-05-14
forum: Programming Talk
---

### Post by fantry on 2006-05-14
root@fantry:~# uname -r 
2.6.12-9-386 
root@fantry:~# apt-get install linux-headers-2.6.12-9-386 
Reading package lists... Done 
Building dependency tree... Done 
linux-headers-2.6.12-9-386 is already the newest version. 
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded. 
root@fantry:~# cd /usr/src/sbull/ 
root@fantry:/usr/src/sbull# ls -l 
total 28 
-rw-r--r-- 1 root src 682 2006-05-14 17:16 Makefile 
-rw-r--r-- 1 root src 10663 2006-05-14 16:59 sbull.c 
-rw-r--r-- 1 root src 2025 2006-05-14 16:59 sbull.h 
-rw-r--r-- 1 root src 1146 2006-05-14 16:59 sbull_load 
-rw-r--r-- 1 root src 184 2006-05-14 16:59 sbull_unload 
root@fantry:/usr/src/sbull# cat Makefile 
# Comment/uncomment the following line to disable/enable debugging 
#DEBUG = y 


# Add your debugging flag (or not) to CFLAGS 
ifeq ($(DEBUG),y) 
DEBFLAGS = -O -g -DSBULL_DEBUG # "-O" is needed to expand inlines 
else 
DEBFLAGS = -O2 
endif 

CFLAGS += $(DEBFLAGS) 
CFLAGS += -I.. 

ifneq ($(KERNELRELEASE),) 
# call from kernel build system 

obj-m := sbull.o 

else 

KERNELDIR ?= /lib/modules/$(shell uname -r)/build 
PWD := $(shell pwd) 

default: 
$(MAKE) -C $(KERNELDIR) M=$(PWD) modules 

endif 



clean: 
rm -rf *.o *~ core .depend .*.cmd *.ko *.mod.c .tmp_versions 

depend .depend dep: 
$(CC) $(CFLAGS) -M *.c > .depend 


ifeq (.depend,$(wildcard .depend)) 
include .depend 
endif 
root@fantry:/usr/src/sbull# make 
make -C /lib/modules/2.6.12-9-386/build M=/usr/src/sbull modules 
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found 
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found 
make[1]: gcc-3.4: Command not found 
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386' 
CC [M] /usr/src/sbull/sbull.o 
/bin/sh: gcc-3.4: command not found 
make[2]: *** [/usr/src/sbull/sbull.o] Error 127 
make[1]: *** [_module_/usr/src/sbull] Error 2 
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386' 
make: *** [default] Error 2 
root@fantry:/usr/src/sbull# 
gcc -v 
Using built-in specs. 
Target: i486-linux-gnu 
Configured with: ../src/configure -v --enable-languages=c,c++,java,f95,objc,ada,treelang --prefix=/usr --with-gxx-include-dir=/usr/include/c++/4.0.2 --enable-shared --with-system-zlib --libexecdir=/usr/lib --enable-nls --without-included-gettext --enable-threads=posix --program-suffix=-4.0 --enable-__cxa_atexit --enable-libstdcxx-allocator=mt --enable-clocale=gnu --enable-libstdcxx-debug --enable-java-gc=boehm --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.4.2-gcj-4.0-1.4.2.0/jre --enable-mpfr --disable-werror --enable-checking=release i486-linux-gnu 
Thread model: posix 
gcc version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9) 
root@fantry:/usr/src/sbull# 

[SIZE="7"]why couldn't i pass the compile?
is it the gcc's version problem?
if it is,when put "gcc -DMODULE -D__KERNEL__ -O2 -Wall -c -I/usr/src/linux-headers.2.6.12-9-386/include hello.c" the problem remain.[/SIZE]
oh my god!!![/COLOR]
In file included from /usr/src/linux-headers-2.6.12-9-386/include/asm/processor.h:18, 
from /usr/src/linux-headers-2.6.12-9-386/include/asm/thread_info.h:17, 
from /usr/src/linux-headers-2.6.12-9-386/include/linux/thread_info.h:21, 
from /usr/src/linux-headers-2.6.12-9-386/include/linux/spinlock.h:12, 
from /usr/src/linux-headers-2.6.12-9-386/include/linux/capability.h:45, 
from /usr/src/linux-headers-2.6.12-9-386/include/linux/sched.h:7, 
from /usr/src/linux-headers-2.6.12-9-386/include/linux/module.h:10, 
from hello.c:2: 
/usr/src/linux-headers-2.6.12-9-386/include/asm/system.h: In function ‘__set_64bit_var’: 
/usr/src/linux-headers-2.6.12-9-386/include/asm/system.h:193: warning: dereferencing type-punned pointer will break strict-aliasing rules 
/usr/src/linux-headers-2.6.12-9-386/include/asm/system.h:193: warning: dereferencing type-punned pointer will break strict-aliasing rules 
root@fantry:/usr/src# insmod hello.o 
insmod: error inserting 'hello.o': -1 Invalid module format 
[SIZE="7"]i have tried it for a long time ,help!!![/SIZE]

---

### Post by Sutekh on 2006-05-15
The Ubuntu kernel was compiled with the GNU C Compiler v3.4 (gcc-3.4) not gcc-4.0, which it seems you have installed.

First install the older compiler
```
sudo apt-get install gcc-3.4
```
Then use these commands to export the older compiler
```
CC=gcc-3.4
export CC
```
Then try the make command again.  Hopefully it will make this time for you.

If you still have problems, please try not shouting with large text, it actually makes things alot harder to read and understand.  

Good luck.

---

### Post by fantry on 2006-05-15
[QUOTE=Sutekh]The Ubuntu kernel was compiled with the GNU C Compiler v3.4 (gcc-3.4) not gcc-4.0, which it seems you have installed.

First install the older compiler
```
sudo apt-get install gcc-3.4
```
Then use these commands to export the older compiler
```
CC=gcc-3.4
export CC
```
Then try the make command again.  Hopefully it will make this time for you.

If you still have problems, please try not shouting with large text, it actually makes things alot harder to read and understand.  

Good luck.[/QUOTE]
the problem has been resolved perfectly with your detailed guide.
forgive me using the large text last time :-D 
[SIZE="7"]"thanks" [/SIZE]

---

### Post by Sutekh on 2006-05-16
I'm glad you solved the problem.  I guess I can allow the large text just this one last time! ;)

---

