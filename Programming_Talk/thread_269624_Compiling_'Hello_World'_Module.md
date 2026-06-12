---
title: "Compiling 'Hello World' Module"
date: 2006-10-02
forum: Programming Talk
---

### Post by ZDemon on 2006-10-02
Hi there.

I've been trying to compile a hello world module based on "linux device drivers 3rd edition" ebook, but to no success. i just cant get it compiled.

i am VERY new to linux, but i know all the basic knowledge and theory. C/C++, kernel space, user space, etc.

This is my program (hello.c):

```
#include <linux/init.h>
#include <linux/module.h>

MODULE_LICENSE("Dual BSD/GPL");

static int hello_init(void)
{
    printk(KERN_ALERT "Hello, world\n");
    return 0;
}
static void hello_exit(void)
{
    printk(KERN_ALERT "Goodbye, cruel world\n");
}

module_init(hello_init);
module_exit(hello_exit);
```


And this is my makefile :

```
ifneq ($(KERNELRELEASE),)
     obj-m := hello.o
else
     KERNELDIR ?= /lib/modules/$(shell uname -r)/build
     PWD := $(shell pwd)
default:
     $(MAKE) -C $(KERNELDIR) M=$(PWD) modules
endif

```


I use dapper drake, and i have the linux-header package. the code on top are directly taken from the book. I'm sorry if this question is too basic.

ANY help would be appreciated. Thanks.

---

### Post by amo-ej1 on 2006-10-02
does 

```

/lib/modules/`uname -r`/build 

```

exist ?

As in 'do you have the kernel source installed' ? Building modules relies on the kernel build system (and thus on the kernel sources to be present).

---

### Post by ZDemon on 2006-10-02
hi there, 

well, i THINK i have them. I apt-get the linux-header packages. Is it more to that? i got the linux-header and linux-header-386 packages.

I dont really understand which header files are needed, maybe thats the problem. The thing is, i cant find any source that tells me what are those files.

Besides, when i run the makefile it says

```
make: Nothing to be done for `default'.
```

Can anyone explain to me where im wrong? is ubuntu different from other distros in the sense that i have to modify the source or the makefile?

Thanks for the quick reply.

---

### Post by amo-ej1 on 2006-10-03
i don't think the headers alone are sufficient, i guess you really need the entire source

---

### Post by ZDemon on 2006-10-03
guys....

im really sorry. i just found out my mistake

everything is correct, except.....I didnt use TAB in the makefile!! It was SPACE instead!!

this is beacuse i directly copied and pasted the code from the PDF book (which is free btw). So the spaces which is supposed to be TABs were SPACE.

example (using spaces at beginning) :
   $(MAKE) -C $(KERNELDIR) M=$(PWD) modules

should be (using TAB, not SPACE):
	$(MAKE) -C $(KERNELDIR) M=$(PWD) modules


I hope other newbies will learn from my silly mistake.
Thanks for the help, amo-ej1.

---

