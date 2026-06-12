---
title: "make for a simple helloworld module returning errors"
date: 2018-12-04
forum: New to Ubuntu
---

### Post by anji1921389 on 2018-12-04
Hello,
I'm new to linux. I started with hello world LKModule. When i tried to run make it showed up many errors. Hope you can help me with this. BTW i'm using Ubuntu18.04 in a virual machine.

When i ran the make command earlier, it showed something like below.
```
anji@anji-VirtualBox:~/Desktop/Anji$ make
make -C /lib/modules/4.15.0-39-generic/build  SUBDIRS=/home/anji/Desktop/Anji modules
make[1]: Entering directory '/usr/src/linux-headers-4.15.0-39-generic'
Makefile:975: "Cannot use CONFIG_STACK_VALIDATION=y, please install libelf-dev, libelf-devel or elfutils-libelf-devel"
  CC [M]  /home/anji/Desktop/Anji/test.o
cc1: error: code model kernel does not support PIC mode
scripts/Makefile.build:339: recipe for target '/home/anji/Desktop/Anji/test.o' failed
make[2]: *** [/home/anji/Desktop/Anji/test.o] Error 1
Makefile:1551: recipe for target '_module_/home/anji/Desktop/Anji' failed
make[1]: *** [_module_/home/anji/Desktop/Anji] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-39-generic'
Makefile:4: recipe for target 'all' failed
make: *** [all] Error 2
```

For this, i added a patch to the kernel makefile (Googled for this issue and found a patch to fix this ***Link:[https://lists.ubuntu.com/archives/kernel-team/2016-May/077178.html](https://lists.ubuntu.com/archives/kernel-team/2016-May/077178.html)). After this patch, the make file is generating many errors. 

```
ake -C /lib/modules/4.15.0-39-generic/build  SUBDIRS=/home/anji/Desktop/Anji modules
make[1]: Entering directory '/usr/src/linux-headers-4.15.0-39-generic'
Makefile:982: "Cannot use CONFIG_STACK_VALIDATION=y, please install libelf-dev, libelf-devel or elfutils-libelf-devel"
  CC [M]  /home/anji/Desktop/Anji/test.o
In file included from ./include/linux/list.h:5:0,
                 from ./include/linux/module.h:9,
                 from /home/anji/Desktop/Anji/test.c:1:
./include/linux/types.h:17:9: error: unknown type name &#8216;__kernel_ino_t&#8217;
 typedef __kernel_ino_t  ino_t;
         ^~~~~~~~~~~~~~
./include/linux/types.h:18:9: error: unknown type name &#8216;__kernel_mode_t&#8217;
 typedef __kernel_mode_t  mode_t;
         ^~~~~~~~~~~~~~~
./include/linux/types.h:21:9: error: unknown type name &#8216;__kernel_off_t&#8217;
 typedef __kernel_off_t  off_t;
         ^~~~~~~~~~~~~~
./include/linux/types.h:22:9: error: unknown type name &#8216;__kernel_pid_t&#8217;
 typedef __kernel_pid_t  pid_t;
         ^~~~~~~~~~~~~~
./include/linux/types.h:23:9: error: unknown type name &#8216;__kernel_daddr_t&#8217;
 typedef __kernel_daddr_t daddr_t;
         ^~~~~~~~~~~~~~~~
./include/linux/types.h:25:9: error: unknown type name &#8216;__kernel_suseconds_t&#8217;
 typedef __kernel_suseconds_t suseconds_t;
         ^~~~~~~~~~~~~~~~~~~~
./include/linux/types.h:26:9: error: unknown type name &#8216;__kernel_timer_t&#8217;
 typedef __kernel_timer_t timer_t;
         ^~~~~~~~~~~~~~~~
./include/linux/types.h:27:9: error: unknown type name &#8216;__kernel_clockid_t&#8217;
 typedef __kernel_clockid_t clockid_t;
         ^~~~~~~~~~~~~~~~~~
./include/linux/types.h:32:9: error: unknown type name &#8216;__kernel_uid32_t&#8217;
 typedef __kernel_uid32_t uid_t;
         ^~~~~~~~~~~~~~~~
./include/linux/types.h:33:9: error: unknown type name &#8216;__kernel_gid32_t&#8217;
 typedef __kernel_gid32_t gid_t;
         ^~~~~~~~~~~~~~~~
./include/linux/types.h:34:9: error: unknown type name &#8216;__kernel_uid16_t&#8217;
 typedef __kernel_uid16_t        uid16_t;
         ^~~~~~~~~~~~~~~~
./include/linux/types.h:35:9: error: unknown type name &#8216;__kernel_gid16_t&#8217;
 typedef __kernel_gid16_t        gid16_t;
         ^~~~~~~~~~~~~~~~
./include/linux/types.h:41:9: error: unknown type name &#8216;__kernel_old_uid_t&#8217;
 typedef __kernel_old_uid_t old_uid_t;
         ^~~~~~~~~~~~~~~~~~
./include/linux/types.h:42:9: error: unknown type name &#8216;__kernel_old_gid_t&#8217;
 typedef __kernel_old_gid_t old_gid_t;
         ^~~~~~~~~~~~~~~~~~
./include/linux/types.h:46:9: error: unknown type name &#8216;__kernel_loff_t&#8217;
 typedef __kernel_loff_t  loff_t;
         ^~~~~~~~~~~~~~~
./include/linux/types.h:55:9: error: unknown type name &#8216;__kernel_size_t&#8217;
 typedef __kernel_size_t  size_t;
         ^~~~~~~~~~~~~~~
./include/linux/types.h:60:9: error: unknown type name &#8216;__kernel_ssize_t&#8217;
 typedef __kernel_ssize_t ssize_t;
         ^~~~~~~~~~~~~~~~
./include/linux/types.h:65:9: error: unknown type name &#8216;__kernel_ptrdiff_t&#8217;
 typedef __kernel_ptrdiff_t ptrdiff_t;
         ^~~~~~~~~~~~~~~~~~
./include/linux/types.h:70:9: error: unknown type name &#8216;__kernel_time_t&#8217;
 typedef __kernel_time_t  time_t;
         ^~~~~~~~~~~~~~~
./include/linux/types.h:75:9: error: unknown type name &#8216;__kernel_clock_t&#8217;
 typedef __kernel_clock_t clock_t;
         ^~~~~~~~~~~~~~~~
./include/linux/types.h:80:9: error: unknown type name &#8216;__kernel_caddr_t&#8217;
 typedef __kernel_caddr_t caddr_t;
         ^~~~~~~~~~~~~~~~
./include/linux/types.h:199:2: error: unknown type name &#8216;__kernel_daddr_t&#8217;
  __kernel_daddr_t f_tfree;
  ^~~~~~~~~~~~~~~~
./include/linux/types.h:200:2: error: unknown type name &#8216;__kernel_ino_t&#8217;
  __kernel_ino_t  f_tinode;
  ^~~~~~~~~~~~~~
In file included from ./include/linux/list.h:9:0,
                 from ./include/linux/module.h:9,
                 from /home/anji/Desktop/Anji/test.c:1:
./include/linux/kernel.h:6:10: fatal error: stdarg.h: No such file or directory
 #include <stdarg.h>
          ^~~~~~~~~~
compilation terminated.
scripts/Makefile.build:339: recipe for target '/home/anji/Desktop/Anji/test.o' failed
make[2]: *** [/home/anji/Desktop/Anji/test.o] Error 1
Makefile:1558: recipe for target '_module_/home/anji/Desktop/Anji' failed
make[1]: *** [_module_/home/anji/Desktop/Anji] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-39-generic'
Makefile:4: recipe for target 'all' failed
make: *** [all] Error 2
anji@anji-VirtualBox:~/Desktop/Anji$
```


Thanks in advance.

---

### Post by TheFu on 2018-12-04
If you need to patch the kernel, I doubt it is hello-world.c
"Hello World" in C is 4 lines.

If you want help with C, please post C code.
If you want help with make, please post the Makefile.

I don't know about 18.04, but for most prior releases there's a set of dependencies to load for C development on the platform.  [https://help.ubuntu.com/community/InstallingCompilers](https://help.ubuntu.com/community/InstallingCompilers) has the details.

---

### Post by anji1921389 on 2018-12-05
Module code:
#include <linux/module.h>
#include <linux/version.h>
#include <linux/kernel.h>
#include <linux/init.h>
int val = 10;
int init_mod(void) {
    printk("Func invoked\n");
    printk("Val = %d\n", val);
}

void exit_mod(void) {
     printk("Module removed\n");
}
module_init(init_mod);
module_exit(exit_mod);
MODULE_AUTHOR("Anjan Reddy");
MODULE_DESCRIPTION("Test Module");


Make file:
obj-m =test.o
KDIR= /lib/modules/$(shell uname -r)/build
all:
        $(MAKE) -C $(KDIR)  SUBDIRS=$(PWD) modules
clean:
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean


And make is failing with the above mentioned errors. I tried installing linux headers, but it didn't help

---

