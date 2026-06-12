---
title: "buidling modules error??"
date: 2008-07-27
forum: Programming Talk
---

### Post by raedbenz on 2008-07-27
I get this when i : 
```
$insmod hell.ko
hello: no version for "struct_module" found: kernel tainted. 
```
any hints?
thanks

---

### Post by lswb on 2008-07-27
What is the hell module? Is it something you compiled yourself? Try resetting your module dependencies byt running:

  sudo depmod

and then to ensure any other modules it depends on are loaded, load it with

sudo modprobe hell

rather than insmod,

---

### Post by raedbenz on 2008-07-27
well
it is a hello.c module

---

### Post by Bachstelze on 2008-07-27
Moved to Programming Talk. Building your own module certainly does not belong in ABT.

---

### Post by dwhitney67 on 2008-07-27
> **raedbenz said:**
> I get this when i : 
```
$insmod hell.ko
hello: no version for "struct_module" found: kernel tainted. 
```
any hints?
thanks
I would have a hint if you listed your code.

Here's a simple HelloWorld.c module that does compile and will run:
[PHP]#include <linux/module.h>      // Needed by all modules

static int __init hello_world( void )
{
  printk( "hello world!\n" );
  return 0;
}

static void __exit goodbye_world( void )
{
  printk( "goodbye world!\n" );
}

module_init( hello_world );
module_exit( goodbye_world );[/PHP]
To build it, create this Makefile and then run 'make':
```
obj-m += HelloWorld.o

all:
        $(MAKE) -C /lib/modules/`uname -r`/build M=$(PWD) modules

clean:
        $(MAKE) -C /lib/modules/`uname -r`/build M=$(PWD) clean
        $(RM) Module.markers modules.order
```
Then as lswb indicated, load the module:
```
$ sudo modprobe HelloWorld
```
When you are done, unload it:
```
$ sudo rmmod HelloWorld
```

P.S.  You should avoid using 'insmod'; it is not very versatile as a stand-alone application.  'modprobe' was designed to use 'insmod', but also perform the necessary dependency checks necessary to load a module, thus loading additional modules if necessary.

---

### Post by raedbenz on 2008-07-27
the code is exactly as the above one, simple hello module.
but i have found on the net that CONFIG_MODVERSIONS should be the same in my PC and the modules. how can i check that??

thankss

---

### Post by dwhitney67 on 2008-07-27
I haven't a clue as to what you are asking.  Try the code I have given, let me know the results.  The code I have shown runs on both Fedora 9 and Ubuntu 8.04.

P.S.  I assume that you have the source code on your system for the kernel that is currently running.

---

### Post by raedbenz on 2008-07-27
well i have tested it and i get the output of printk(), but i get this as well:
hello: no version for "struct_module" found: kernel tainted.

---

### Post by dwhitney67 on 2008-07-27
Show me your code.

Show me your Makefile, or the command line statement that you are using to build your module.

Show me the version of the Linux Kernel you are using.
```
$ uname -r
```

Do you have the Linux Kernel source code?  Verify by:
```

$ cd /lib/modules/`uname -r`/build
$ cd /usr/src/kernels/`uname -r`

```

---

### Post by raedbenz on 2008-07-27
> **dwhitney67 said:**
> Show me your code.

Show me your Makefile, or the command line statement that you are using to build your module.
```
obj-m := hello.o

KDIR    := /lib/modules/$(shell uname -r)/build
PWD    := $(shell pwd)

default:
	$(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules

```

```
raed@raed-laptop:~$ cd /lib/modules/`uname -r`/build
raed@raed-laptop:/lib/modules/2.6.24-19-generic/build$ 

```
> $ cd /usr/src/kernels/`uname -r`
```
raed@raed-laptop:~$ cd /usr/src/kernels/`uname -r`
bash: cd: /usr/src/kernels/2.6.24-19-generic: No such file or directory

```
bcoz i have these two:
/usr/src/linux-headers-2.6.24-19
/usr/src/linux-headers-2.6.24-19-generic

thanks

---

### Post by dwhitney67 on 2008-07-27
Ok, first of all, I have witnessed a difference in behaviour between using my Makefile and yours.  With your Makefile, I get the following written to /var/log/messages when I load the kernel module:
```
Jul 27 12:16:16 localhost kernel: HelloWorld: module license 'unspecified' taints kernel.
Jul 27 12:16:16 localhost kernel: hello world!
```
When I use my Makefile, which specifies an M in lieu of SUBDIRS, then I do not get the first message concerning the module license (by the way, this is caused because I have not specified a GPL-license thingy in the source file.)  This is on my Fedora 9 system; on Ubuntu 8.04 I do not get the GPL warning.

The other thing, I found out, is that I was incorrect in instructing you to use 'modprobe'.  You are correct, 'insmod' should be used.  The 'modprobe' command should only be used if the kernel module is in a known area, namely /lib/modules/`uname -r`, and in other areas specified in /etc/modprobe.conf.

Anyhow, the /lib/modules/`uname -r`/build directory should point to your /usr/src/linux-headers-`uname -r` directory.  Seems every distro tends to place their kernel sources in a different area, however the 'build' directory should always reference the particular directory.

So to summarize, if you are using the same HelloWorld.c kernel module source code, then these steps should work for you:
```
$ make
$ sudo insmod ./HelloWorld.ko
$ sudo tail /var/log/messages
$ sudo rmmod HelloWorld
$ sudo tail /var/log/messages
```
If there is still a problem, then I haven't a clue.  I have the same kernel version you have, along with the source code, as given by the system update back on 16-July-08 or so.

---

### Post by raedbenz on 2008-07-27
plz check this post , thats what i meant before regarding version inconsistency CONFIG_MODVERSIONS.[http://lkml.org/lkml/2005/6/22/1]("http://lkml.org/lkml/2005/6/22/1")
thanks

---

### Post by dwhitney67 on 2008-07-27
I read the post, but it does not mean anything to me.  I am/was not building my kernel module using anything different than I showed you; that is, I was not specifying any kernel option(s).

You can verify your kernel option with this command:
```
$ grep CONFIG_MODVERSIONS /boot/config-`uname -r`
```
CONFIG_MODVERSIONS will undoubtedly be set to '=y'.

Like I said, I don't know what is wrong with your system.  We have the same kernel, and presumably the same kernel source code.  On my Ubuntu 8.04 system, when I build the module and then insert (load) it, I do not get the warning message you see on your system.

On my Fedora 9 system, I get the GPL-warning, but only when I use your Makefile.  When I use the Makefile I posted earlier, I do not get the warning.

---

### Post by raedbenz on 2008-07-28
> obj-m += HelloWorld.o

all:
        $(MAKE) -C /lib/modules/`uname -r`/build M=$(PWD) modules

clean:
        $(MAKE) -C /lib/modules/`uname -r`/build M=$(PWD) clean
        $(RM) Module.markers modules.order
hi
assume i want to use optimization level -O2. where do I specify that?
is it inside makefile or when building module with
```
make -O2
```???
thanks

---

### Post by dwhitney67 on 2008-07-28
I have never tried optimizing a kernel module, perhaps because the ones I have worked with were quite simple.

Nevertheless, I believe you need to define EXTRA_CFLAGS=-O2 into the Makefile, somewhere before the 'all' entry point.

```
obj-m += HelloWorld.o

EXTRA_CFLAGS = -O2

all:
        $(MAKE) -C /lib/modules/`uname -r`/build M=$(PWD) modules

clean:
        $(MAKE) -C /lib/modules/`uname -r`/build M=$(PWD) clean
        $(RM) Module.markers modules.order
```

P.S.  Refer to the attachment for a good tutorial about building Linux Kernel Modules (someone else posted it once here on Ubuntu Forums).

---

