---
title: "Not able to build the kernel module using make"
date: 2008-09-14
forum: Programming Talk
---

### Post by akshata on 2008-09-14
Hi,
I have witten the following C program test.c for kernel 2.6 

#include <linux/module.h> 
#include <linux/kernel.h> 
int init_module(void)
{
printk(KERN_INFO "Hello world 1.\n");
return 0;
}
void cleanup_module(void)
{
printk(KERN_INFO "Goodbye world 1.\n");
}


and the coressponding Makefile as

obj&#8722;m += hello&#8722;1.o
all:
make &#8722;C /lib/modules/$(shell uname &#8722;r)/build M=$(PWD) modules
clean:
make &#8722;C /lib/modules/$(shell uname &#8722;r)/build M=$(PWD) clean


When i run a make command in the same directory i get the following output
make: Nothing to be done for 'all'


The test.ko file is not getting created. Please can anyone tell me what the problem is and how to rectify it?

Thanks,
Akshata

---

### Post by dwhitney67 on 2008-09-14
Your Makefile looks like the suspect here.

Statements that are associated with a Makefile entry point (e.g. 'all' and 'clean') need to be indented with a tab-space.  For instance:
```
obj-m += test.o

all:
**<tab>**make &#8722;C /lib/modules/$(shell uname &#8722;r)/build M=$(PWD) modules

clean:
**<tab>**make &#8722;C /lib/modules/$(shell uname &#8722;r)/build M=$(PWD) clean
```
Btw, is your C source-file named "test.c" or "hello-1.c"??  Please update the obj-m section of the Makefile accordingly.

---

### Post by akshata on 2008-09-15
Thanks a lot!! The <tab> did turn out to be the culprit!!

Thanks again..

---

