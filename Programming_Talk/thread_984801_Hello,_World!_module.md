---
title: "Hello, World! module"
date: 2008-11-17
forum: Programming Talk
---

### Post by swappo1 on 2008-11-17
Hello,

I am trying to compile and run my first module.  I am using the following tutorial: [http://tldp.org/LDP/lkmpg/2.6/html/lkmpg.html#AEN121](http://tldp.org/LDP/lkmpg/2.6/html/lkmpg.html#AEN121)  I save the following in hello-1.c:[PHP]/*  
 *  hello-1.c - The simplest kernel module.
 */
#include <linux/module.h>	/* Needed by all modules */
#include <linux/kernel.h>	/* Needed for KERN_INFO */

int init_module(void)
{
	printk(KERN_INFO "Hello world 1.\n");

	/* 
	 * A non 0 return means init_module failed; module can't be loaded. 
	 */
	return 0;
}

void cleanup_module(void)
{
	printk(KERN_INFO "Goodbye world 1.\n");
}[/PHP]
My problem is with the Makefile.  The example provides me with the following:
> obj-m += hello-1.o

all:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean
I created this file in gedit and saved it as hello-1.o. I am not sure if this is what I was supposed to do or not since it is not specific on how to proceed. It then says to "compile the module by issuing the command  make", however I don't know how to do this and I could not find a tutorial on google.  Does anybody know how to compile and run this?  Thanks

---

### Post by Tony Flury on 2008-11-17
the makefile should not be saved as hello-1.0, they are normally just saved with the name "makefile".

.o files are object filesproduced by the compiler - which are then linked together (and with libraries) to produce executables.

to use the makefie once it is created, you should just issue the command
```

make all

```
in a terminal.

Can i ask why you are trying to go down the route of building kernel modules, when you seem to be an almost complete beginner. I would have thought it would be far better to start with userspace application type programs (that don't need kernel stuff), and get your hand in with compilers, linkers, makefiles, libraries etc before going anywhere near kernel stuff.

---

### Post by swappo1 on 2008-11-17
My interests are in building drivers.  I am using the linux device drivers, 3rd edition to learn from.  However, it tells the reader to run a simple printk module but it never explains how to run the module.  So, I am trying to find out how to load and run this simple module to get started.  I have worked with userspace applications over the past couple of months and am interested in now moving into learning drivers.

---

### Post by Tony Flury on 2008-11-17
ok - so you need to create the makefile - like i explained - and then run make all

if you want to know about make files - look at : 
```

man make

```

---

