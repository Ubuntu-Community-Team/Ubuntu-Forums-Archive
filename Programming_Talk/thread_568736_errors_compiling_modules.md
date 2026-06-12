---
title: "errors compiling modules"
date: 2007-10-06
forum: Programming Talk
---

### Post by fr0ike on 2007-10-06
hi,

i want to learn how to build device drivers (kernel modules). so i bought a book and started to read...
i`ve copied some piece of code from the book and tried to compile them, 
but there are some errors popped up i can`t solve myself. i hope you can help me out...

*******************************
module source
*******************************

#define _LINUX_TIME_H 1 //thats to solve the "Redefinition von »struct timespec«" problem

#include <linux/version.h>
#include <linux/module.h>


int init_module(void){
printk("init_module called\n");
return 0;
}

void cleanup_module(void){
printk("cleanup_module called\n");
}

MODULE_LICENSE("GPL");
*******************************

*******************************
Makefile (changed, perhaps its a piece of crap, i`m not very familiar with makefiles)
*******************************
obj-m := mod1.o
mod1.o: mod1.c
*******************************


*******************************
output
*******************************
$make
cc    -c -o mod1.o mod1.c
In Datei, eingefügt von /usr/include/linux/sched.h:16,
                    von /usr/include/linux/module.h:9,
                    von mod1.c:4:
/usr/include/linux/signal.h:2:2: Warnung: #warning "You should include <signal.h>. This time I will do it for you."
In file included from mod1.c:4:
/usr/include/linux/module.h:41: Fehler: Feld »attr« hat unvollständigen Typen
/usr/include/linux/module.h:49: Fehler: Feld »kobj« hat unvollständigen Typen
make: *** [mod1.o] Fehler 1
*******************************

*******************************
Makefile from book
*******************************
ifneq ($(KERNELRELEASE),)
obj-m := mod1.o

else:
KDIR := /lib/modules/$(shell uname -r)/build
PWD := $(shell pwd)

default:
        $(MAKE) -C $(KDIR) M=$(PWD) modules
endif
*******************************

*******************************
output
*******************************
$make
make: *** Keine Targets.  Schluss.
*******************************


some info:

linux-headers-2.6.15-29-686
linux-source-2.6.15
ubuntu 6.06 "dapper drake"
gcc-Version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)


Thanks in advance!
fr0ike

---

### Post by moma on 2007-10-06
Hello,

**Try this **

File:**mod1.c**
```

/* 
#define _LINUX_TIME_H 1 
thats to solve the "Redefinition von »struct timespec«" problem
*/

#include <linux/version.h>
#include <linux/kernel.h>
#include <linux/module.h>
#include <linux/moduleparam.h>

#include <linux/time.h>

#include <linux/init.h>
#include <linux/stat.h> 


MODULE_LICENSE("GPL");
MODULE_AUTHOR("Kalle & Olga Kuusamolainen"); 

static int __init init_this_module(void)
{
     	printk(KERN_INFO "mod1: init_this_module() called.\n");
	return 0;
}

static void __exit  shutdown_this_module(void)
{
     	printk(KERN_INFO "mod1: shutdown_this_module() called.\n");
}


module_init(init_this_module);
module_exit(shutdown_this_module);  
```

File:**Makefile **
```
obj-m  := mod1.o

KDIR   := /lib/modules/$(shell uname -r)/build
PWD    := $(shell pwd)

default:
	$(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules
```

Note:
In the Makefile, there must be a TAB (tabulator) character before the 
[COLOR="DimGray"]$(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules[/COLOR]
line.


**Compile it (using the Makefile):**
$ [COLOR="green"]make [/COLOR]

**Load the module mod1.ko:**
$ [COLOR="green"]sudo insmod mod1.ko[/COLOR]

**Now check the system messages**
$ [COLOR="green"] dmesg | tail -10[/COLOR]

[COLOR="black"][13408.233936] mod1: init_this_module() called.[/COLOR]

**Remove the module:** 
$ [COLOR="Green"]sudo rmmod mod1[/COLOR]

**Check again the system messages**
$ [COLOR="green"] dmesg | tail -10[/COLOR]
or 
$ [COLOR="green"] dmesg | grep "mod1" [/COLOR]

[COLOR="black"][13408.233936] mod1: init_this_module() called.
[13408.233937] mod1: shutdown_this_module() called.[/COLOR]

[COLOR="red"]Very important:[/COLOR]  Study these kernel developers' guides
[http://www.futuredesktop.org/kernel.html](http://www.futuredesktop.org/kernel.html)   Section: Driver and module programming.

Good luck ;-)
-----------------------

EDIT: Prerequisites to compile a kernel-module are:
$ [COLOR="SeaGreen"]sudo aptitude install build-essential gdb  linux-headers-$(uname -r)[/COLOR]

You may also need:
$ [COLOR="SeaGreen"]sudo aptitude install automake autoconf libtool[/COLOR]
-----------------------

ps. This is howto install VMware Player and VirtualBox in/on Ubuntu 7.10 beta (gutsy gibbon).
[http://www.futuredesktop.org/vmware/vmware-player-gutsy.html](http://www.futuredesktop.org/vmware/vmware-player-gutsy.html)  (just in case you need some love)

---

### Post by fr0ike on 2007-10-06
wow...
works perfectly ! thanks a lot !

---

