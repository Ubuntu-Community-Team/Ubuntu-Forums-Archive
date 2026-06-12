---
title: "Help: My first kernel module"
date: 2007-09-10
forum: Programming Talk
---

### Post by kvorion on 2007-09-10
I am trying to compile my first hello world kernel module. I realized that I did not have the linux kernel source, so I downloaded it. 

```

#define MODULE
#include <linux/module.h>
int init_module(void) { printk("<1>Hello, world\n"); return 0; }
void cleanup_module(void) { printk("<1>Goodbye cruel world\n"); }

```

The problem is that gcc is not able to find linux/module.h file inside /usr/include/iinux folder (which I believe is the default path). How do I like gcc to the file inside the /usr/src/linux-source-2.6.15-2.6.15/include/linux folder where the file actually is? (I created this folder by extracting from the source archive that I downloaded). Where should I extract this so that gcc can actually find it?

---

### Post by CptPicard on 2007-09-10
Would be easier for you to download the sources using apt from the repositories, and in particular, install the kernel-headers package.

---

### Post by kvorion on 2007-09-10
I also used the makefile method of compiling the code, but I got the following error:

make: Nothing to be done for 'all'. I checked out this page: [http://www.captain.at/programming/kernel-2.6/](http://www.captain.at/programming/kernel-2.6/)

and it said that the kernel source has to be installed. What does that mean? Is there a guide that lists the exact steps to be done before I can start compiling kernel modules? The dont seem to be able to figure out what exactly the pre-requisites are.

---

### Post by gnusci on 2007-09-10
first of all make sure you did download the [COLOR="Red"]kernel[/COLOR] source according to you actual kernel:

**> uname -a **

Now if you gcc is looking for the libraries in:

**/usr/include/linux**

just make a symbolic link to the right path:

**> ln -s /usr/src/linux-source-2.6.15-2.6.15/include/linux /usr/include/linux**

make sure that there is not a:

**/usr/include/linux**

symbolic link first.

EDIT: maybe you will need to compile a new kernel if you want to use a new one, but I will suggest you to take **CptPicard** advising.

---

### Post by fct on 2007-09-11
You don't need to compile a new kernel. Just the kernel-headers package of your current kernel is enough.

And the linked tutorial doesn't seem right to me, specially the KDIR part. I compile my modules like this:

**Makefile:**

*obj-m := modulename.o*

**Command:**

*$ make -C /usr/src/linux-headers-`uname -r` SUBDIRS=$PWD modules*

---

