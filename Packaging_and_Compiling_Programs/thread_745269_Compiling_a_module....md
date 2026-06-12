---
title: "Compiling a module..."
date: 2008-04-04
forum: Packaging and Compiling Programs
---

### Post by POW R TOC H on 2008-04-04
I am learning to write kernel modules. I have downloaded and 'installed' kernel source tree, but something's wrong...

I used this example from this[http://tldp.org/LDP/lkmpg/2.6/html/x121.html]("http://tldp.org/LDP/lkmpg/2.6/html/x121.html") link.
This is the source :
```

#include <linux/module.h>
#include <linux/kernel.h>

int init_module(void)
{
	printk("<1>Hello world (1)!\n");
	return 0;
}

void cleanup_module(void)
{
printk(KERN_ALERT "Goodbye cruel woeld (1)!\n");
}
```

and this is the Makefile :
```

obj-m += hello-1.o

all:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

```
It compiled it, and I had a few files in my folder :
 hello-1.ko     hello-1.mod.o  hello-1.mod.c  hello-1.o Module.symvers

I used the command insmode ./hello-1.ko to load the module, and it worked, and the module was loaded (lsmod displayed it). Then, I used rmmod to remove it.

As you can see, in printk function, I printed the message in top priority, but it didn't show in the console (nor did it appear in /var/log/messages)... 
I tried using modprobe to insert the module, but it returned this :
FATAL: Module ./hello_1.ko not found.

What is causing this? 
Thank you in advance...

---

### Post by geraldm on 2008-04-04
modprobe needs the module location and dependency information in 
/lib/modules/`uname -r`/modules.dep
The module installation was incomplete.  The module also needs to be in the location stated in modules.dep.

The module example you are using is old; it was used in early kernel 2.6 styles.  Newer modules use module license information and 
different macro.  Look into the modules in the kernel source for 
examples of the newer style.

Gerald

---

### Post by POW R TOC H on 2008-04-04
Thank you. Would you also be kind to point me to some books about the (new) modules, and the kernel, in general?

---

### Post by geraldm on 2008-04-06
One book, available under Creative Commons license:
[http://www.kroah.com/lkn](http://www.kroah.com/lkn)
Other places that track the kernel are in:
[http://www.lwn.net](http://www.lwn.net)

Gerald

---

