---
title: "writing a trivial kernel module - help"
date: 2010-05-28
forum: Programming Talk
---

### Post by sonicbs on 2010-05-28
Hi, I am trying to learn how to write a kernel module.
I am following the excellent guide from [The Linux Documentation Project]("http://tldp.org/") called [The Linux Kernel Module Programming Guide v.2.6.4]("http://tldp.org/LDP/lkmpg/2.6/html/index.html").

My machine is running Ubuntu Lucid Lynx (10.04)
```
uname -r
2.6.32-22-generic
```

I installed the corresponding linux headers and just to make sure I also installed the linux source and extracted it in /usr/src

I am trying to run the following trivial kernel module
```
/*  
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
	printk(KERN_ALERT "Goodbye world 1.\n");
}
```

with the following Makefile
```
obj&#8722;m += hello&#8722;1.o
all:
	make &#8722;C /lib/modules/$(shell uname &#8722;r)/build M=$(PWD) modules
clean:
	make &#8722;C /lib/modules/$(shell uname &#8722;r)/build M=$(PWD) clean
```
as it appears in pages 5 and 6 of the pdf version of the tutorial above.
I got the following error from make
```
uname: extra operand `&#8722;r'
Try `uname --help' for more information.
make &#8722;C /lib/modules//build M=/home/sonny/km modules
make[1]: Entering directory `/home/sonny/km'
make[1]: *** No rule to make target `&#8722;C'.  Stop.
make[1]: Leaving directory `/home/sonny/km'
make: *** [all] Error 2
```
So, from the first and third lines I saw there was a problem with uname -r
so I changed the Makefile to
```
obj&#8722;m += hello-1.o
KVERSION = $(shell uname -r)
all:
	make &#8722;C /lib/modules/$(KVERSION)/build M=$(PWD) modules
clean:
	make &#8722;C /lib/modules/$(KVERSION)/build M=$(PWD) clean
```
and then running make corrected the first error, but I still get the following:
```
make &#8722;C /lib/modules/2.6.32-22-generic/build M=/home/sonny/km modules
make[1]: Entering directory `/home/sonny/km'
make[1]: *** No rule to make target `&#8722;C'.  Stop.
make[1]: Leaving directory `/home/sonny/km'
make: *** [all] Error 2
```

What am I doing wrong? All the headers are in place and the source is there as well.
lib/modules/2.6.32-22-generic links to (what I think are) the right places.
Any help would be much appreciated.

Thanks a lot!

---

### Post by dwhitney67 on 2010-05-28
Your latest version of the Makefile looks good.

Make sure that you have the proper build tools installed on your system:
```

sudo apt-get install build-essential

```

---

### Post by Reiger on 2010-05-28
You'll need to have kernel headers as well:
```

sudo apt-get install linux-header-`uname -r`

```

---

### Post by sonicbs on 2010-05-28
> **Reiger said:**
> You'll need to have kernel headers as well:
```

sudo apt-get install linux-header-`uname -r`

```

Reiger, thanks a lot for the help, but I already have the linux-header package installed.

---

### Post by sonicbs on 2010-05-28
> **dwhitney67 said:**
> Your latest version of the Makefile looks good.

Make sure that you have the proper build tools installed on your system:
```

sudo apt-get install build-essential

```

dwhitney67, thanks a lot for the prompt reply, but I already have the build-essential package installed.
I also tried reinstalling it.

---

### Post by sonicbs on 2010-05-28
Unbelievable... after 48 hours of headbanging it turns out the the hyphens I have in this file are not the right hypens. This messed everything. Let this be a warning to you all... don't copy&paste from a PDF!

---

