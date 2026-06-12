---
title: "Loading my first linux module"
date: 2011-08-14
forum: Packaging and Compiling Programs
---

### Post by katochd46 on 2011-08-14
Hi,

I am trying to load my first linux module.
As per this link :
[http://www.faqs.org/docs/kernel/hello2.html](http://www.faqs.org/docs/kernel/hello2.html)

make file:
> 
WARN    := -W -Wall -Wstrict-prototypes -Wmissing-prototypes
INCLUDE := -isystem /lib/modules/`uname -r`/build/include
CFLAGS  := -O2 -DMODULE -D__KERNEL__ ${WARN} ${INCLUDE}
CC      := gcc-3.0
OBJS    := ${patsubst %.c, %.o, ${wildcard *.c}}

all: ${OBJS}
   
.PHONY: clean

clean:
   rm -rf *.o
Code:
> /*  hello-2.c - Demonstrating the module_init() and module_exit() macros.  This is the
 *     preferred over using init_module() and cleanup_module().
 */
#include <linux/module.h>   // Needed by all modules
#include <linux/kernel.h>   // Needed for KERN_ALERT
#include <linux/init.h>     // Needed for the macros


static int hello_2_init(void)
{
   printk(KERN_ALERT "Hello, world 2\n");
   return 0;
}


static void hello_2_exit(void)
{
   printk(KERN_ALERT "Goodbye, world 2\n");
}


module_init(hello_2_init);
module_exit(hello_2_exit);



Compilation Error :
> make all
gcc-3.0 -O2 -DMODULE -D__KERNEL__ -W -Wall -Wstrict-prototypes -Wmissing-prototypes -isystem /lib/modules/`uname -r`/build/include   -c -o hello-2.o hello-2.c
/bin/sh: gcc-3.0: not found
make: *** [hello-2.o] Error 127


How can i compile it please suggest Question ?

---

### Post by SevenMachines on 2011-08-16
gcc-3.0 is pretty old so unsurprisingly you wont have it on your system. You could try replacing gcc-3.0 with just gcc in your makefile but maybe you should try the following makefile instead

Makefile:
```
obj-m += hello-2.o

all:
  make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
  make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

.PHONY: all, clean

```

---

