---
title: "How to automatically load my driver as kernel boots up"
date: 2007-11-12
forum: Programming Talk
---

### Post by smanikandan14 on 2007-11-12
Hi All,


This query may be simple one...

    Under /dev directory we see many character/block device files were created as soon as the system boots up. The driver code for all those files are present inside /usr/src/linux-2.6.18.35/drivers    (for ex version 2.6.18.35). 

1) Where is the code written to create the devices files under /dev directory. At what stage of booting process of kernel that code is executed so that files under /dev are created. 

2) Suppose if i want to write my sample driver code which does storing of a string and displaying it when read. And i wanted to create a file under /dev as my kernel boots up and load the driver too.. how should i acheive this...

Like i write my .c file in drivers driectory edit the makefile to compile my .c file ? then how shld i proceed ? where and all i shld make changes..  to load my driver automatically as kernel boots up and create a file under /dev directory... 


If any one can suggest me that would be helpful. Just tyring to understand much of kernel source tree.

Thanks in advance.

Regards,
Mani

---

### Post by kidders on 2007-11-14
Hi there,

> **smanikandan14 said:**
> Where is the code written to create the devices files under /dev directory.On modern Linux systems, the contents of /dev are managed by udev.

> **smanikandan14 said:**
> Suppose if i want to write my sample driver codeYou can use tools like insmod to load drivers.

> **smanikandan14 said:**
> Like i write my .c file in drivers driectory edit the makefile to compile my .c file ?Don't modify your kernel source tree. I suggest taking a look at the source of third party drivers (eg Nvidia's display driver) to see how building kernel modules is done.

---

### Post by aquavitae on 2007-11-14
In addition to kidders response, I'd also suggest you have a look at the gentoo docs and wiki, accessable from [http://www.gentoo.org]("http://www.gentoo.org"). I don't know if theres anything on that in particular, but just installing gentoo involves compiling the kernel so there might be something useful.  Its quite a good place to look for low-level linux stuff!

---

### Post by kidders on 2007-11-14
That's a great idea. :-) Gentoo has quite a few ebuilds that compile & install kernel modules from outside the kernel tree (eg pwc & alsa drivers).

---

### Post by smanikandan14 on 2007-11-20
I read few stuffs abt udev filesystem. It is told that udev filesystem manages the /dev directory entries. It maintains entries for the devices which are currently presently in the system.

In that case how do i tell udev to auto load my module whenever my system gets booted. How does the entries in the  /dev are created ( device files which are present as when the system boots up ... who does that )...

Sorry, not getting the over all pic...

- Mani

---

### Post by aquavitae on 2007-11-21
I never really got into the details of it, but I seem to remember the whole process is controlled by some config files in /etc.  I'm pretty sure there's a good gentoo guide on udev - have a look at it and see if it helps.  I've always found that the dev files are created when needed, but that might be because the kernel module tells it to create them.  Also have a look at the mknod command - I think it can be used to manually create /dev entried.

Just to clarify, when you talk about auto loading your module, do you mean a /dev device, or do you mean a kernel module.  Autoloading a kernel module is acompletely different thing and has nothing to do with creating a block device - you load kernel modules with the modprobe command.  I'm not sure of the best way of doing this automatically... maybe a startup script?  Once again, you might find something on that on the gentoo site.

Another attempt to answer your question :): The kernel iteself in compiled as a single executable. Modules for the kernel can be either be compiled into the kernel, or compiled separately and then loaded into the kernel (using modprobe).  As I understand it, some modules (such as hard disk controllers) will call functions to create block devices. I'm not sure exactly how this works, but somehow, it lets udev know that it needs to create a /dev file.  This happens when the module is loaded, so as I see it what you need to do is find out how to automatically load your kernel module at boot up, and how to let udev know it needs to create a device.

Hope you understand this - not sure I explained very well!

---

### Post by dwhitney67 on 2007-11-21
On Ubuntu, you would add the kernel module you are interested in loading during startup within the file /etc/modules.

You should verify that you are able to load a module using "modprobe".  If this command succeeds, you will not see any output, but you can verify the load using "lsmod" (or by examining the return status of the modprobe).

Thus an example is:

```
$ sudo modprobe uname_ix86
$ lsmod | grep uname_ix86
```

Here's an example Linux kernel module, and the Makefile to compile it.  Once it's compiled, there should be a module name called uname_ix86.ko.  The steps to load it were previously shown above.

uname_ix86.c:
```
/*
 *      This simple piece of code simply turns your ix86 into a i586 -
 *      useful if you're cross-compiling for a weaker platform.
 *
 *      Based on the program contained in the cross compiling hint by
 *      Daniel Baumann <danielbaumann@linuxmail.org>
 *                              
 *      Originally Updated to 2.6.x series kernel by Roel Neefs.
 *
 *      Updated to work with the 2.6.x series kernel driver standards
 *      by Jim Gifford.
 *
 *      You will need to create a small Makefile for this module to 
 *      work.
 *
 *              cat > Makefile << "EOF"
 *              obj-m += uname_ix86.o
 *              EOF
 *
 *      To compile as a module use the following command:
 *
 *              make -C /usr/src/linux-{version} SUBDIRS=$PWD
 *
 *      You can change the UNAME_DUMB_STEPPING variable to get the following
 *      results
 *
 *              2 = 286         3 = 386         4 = 486         5 = 586         6 = 686
 *                                                                                      
 */

#include <linux/module.h>
#include <linux/init.h>
#include <linux/utsname.h>

#ifndef UNAME_DUMB_STEPPING
        #define UNAME_DUMB_STEPPING '5';
#endif

static int save;
static int __init uname_hack_init_module( void )
{
  save = utsname()->machine[1];
  utsname()->machine[1] = UNAME_DUMB_STEPPING;
  return( 0 );
}

static void __exit uname_hack_cleanup_module( void )
{
  utsname()->machine[1] = save;
}

module_init(uname_hack_init_module);
module_exit(uname_hack_cleanup_module);
```

Makefile:
```
obj-m += uname_ix86.o
```

---

