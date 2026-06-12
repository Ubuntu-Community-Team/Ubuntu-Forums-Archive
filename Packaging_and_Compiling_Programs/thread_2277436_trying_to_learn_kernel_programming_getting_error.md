---
title: "trying to learn kernel programming getting error"
date: 2015-05-08
forum: Packaging and Compiling Programs
---

### Post by j.j.2 on 2015-05-08
hello,

I am using Ubuntu 14.04.2. I am try to learn kernel programming.

this is my c file:

#include <linux/module.h>
#include <linux/config.h>
#include <linux/init.h>

static int __init mymodule_init(void)
{
 printk ("My module worked!\n");
        return 0;
}

static void __exit mymodule_exit(void)
{
 printk ("Unloading my module.\n");
        return;
}

module_init(mymodule_init);
module_exit(mymodule_exit);

MODULE_LICENSE("GPL");

this is my Makefile:

obj-m := mymodule.o    

KDIR  := /lib/modules/$(shell uname -r)/build

all:
    $(MAKE) -C $(KDIR) M=$(PWD) modules

clean:
    $(MAKE) -C $(KDIR) M=$(PWD) clean
    $(RM) Module.markers modules.order


both my c file and makefile are in usr/src/test

my output//error:
ubuntu@ubuntu:/usr/src/test$ sudo apt-get install linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-3.16.0-30-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 236 not upgraded.
ubuntu@ubuntu:/usr/src/test$ sudo make
make -C /usr/src/linux-headers-3.16.0-30-generic SUBDIRS= modules
make[1]: Entering directory `/usr/src/linux-headers-3.16.0-30-generic'
make[2]: *** No rule to make target `arch/x86/syscalls/syscall_32.tbl', needed by `arch/x86/syscalls/../include/generated/asm/syscalls_32.h'.  Stop.
make[1]: *** [archheaders] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.16.0-30-generic'
make: *** [all] Error 2

can someone help me?

---

### Post by osmoma on 2015-05-09
Hello,
Guide: [http://www.tldp.org/LDP/lkmpg/2.6/html/lkmpg.html#AEN181](http://www.tldp.org/LDP/lkmpg/2.6/html/lkmpg.html#AEN181)

0) Create a working directory in your $HOME (local) folder.  Create testmod1.c and Makefile in that directory. I used gedit editor. 
$ cd $HOME
$ mkdir Test
$ cd Test
----------
1)  Install compiler, linker and make tools. Install also linux-headers.
$ sudo apt-get install build-essential linux-headers-$(uname -r)

2) Create testmod1.c file:
```
#include <linux/module.h>    /* Needed by all modules */
#include <linux/kernel.h>    /* Needed for KERN_INFO */

static int __init mymodule_init(void)
{
    printk(KERN_INFO "testmod1.ko module Loaded.\n");
    return 0;
}

static void __exit mymodule_exit(void)
{
   printk(KERN_INFO "testmod1.ko module UNLoaded.\n");
   return;
}

module_init(mymodule_init);
module_exit(mymodule_exit);

MODULE_LICENSE("GPL");
```

3) Create Makefile  (Makefile with upper case M)

```
obj-m += testmod1.o

all:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean
```

4) Compile and link. Run make.
$ make

make -C /lib/modules/3.19.0-16-generic/build M=/home/moma/Test modules
make[1]: Entering directory '/usr/src/linux-headers-3.19.0-16-generic'
  CC [M]  /home/moma/Test/testmod1.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/moma/Test/testmod1.mod.o
  LD [M]  /home/moma/Test/testmod1.ko
make[1]: Leaving directory '/usr/src/linux-headers-3.19.0-16-generic'
----------

5) Check module information.
$ modinfo testmod1.ko

filename:       /home/moma/Test/testmod1.ko
license:        GPL
srcversion:     B93C955162CEC328B2B91FD
depends:        
vermagic:       3.19.0-16-generic SMP mod_unload modversions 
----------

 6) Load the module (run insmod as sudo)
$ sudo insmod testmod1.ko
----------

7) Check kernel messages (dmesg)
$ dmesg 
$ dmesg | grep testmod1

[ 7620.944820] testmod1.ko module Loaded.
----------

8) List modules with lsmod

$ lsmod 
$ lsmod | grep testmod1
...
testmod1               16384  0 
----------

9) Remove, unload the module (run rmmod as sudo)
$ sudo rmmod testmod1

10) And check the kernel messages
$ dmesg | grep testmod1

[ 7620.944820] testmod1.ko module Loaded.
[ 7818.037029] testmod1.ko module UNLoaded.

Other resources:
[http://lwn.net/Kernel/LDD3/](http://lwn.net/Kernel/LDD3/)

Have fun!
**[COLOR=#ff0000]Ps[/COLOR]**. Check also [audio-recorder...]("https://launchpad.net/~audio-recorder")

---

### Post by j.j.2 on 2015-05-11
still does not work! I am still getting error:

ubuntu@ubuntu:/home/test$ make
make -C /lib/modules/3.13.0-24-generic/build M=/home/test modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
/usr/src/linux-headers-3.13.0-24-generic/arch/x86/Makefile:113: CONFIG_X86_X32 enabled but no binutils support
make[2]: *** No rule to make target `/home/test/testmod1.c', needed by `/home/test/testmod1.o'.  Stop.
make[1]: *** [_module_/home/test] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make: *** [all] Error 2

---

### Post by osmoma on 2015-05-13
Hello,
Maybe you are missing some packages...[COLOR=#111111][FONT=Ubuntu]
[/FONT][/COLOR][COLOR=#000000]$ sudo apt-get install --reinstall [/COLOR]libtool automake autoconf [COLOR=#000000] build-essential linux-headers-$(uname -r)
[/COLOR]

---

