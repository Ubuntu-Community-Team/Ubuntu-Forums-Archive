---
title: "hello world module problem"
date: 2011-01-05
forum: Programming Talk
---

### Post by chuchi on 2011-01-05
Hello friends! I'm following the guide "The linux kernel module  programming guide". I'm trying with the hello world mode, wich code is  this:
```

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


```

And this is the Makefile:

```

obj-m += hello.o
all:
	make -C /lib/modules/2.6.32-27-generic/build M=/home/jesus/pruebas/c modules
clean:
	make -C /lib/modules/2.6.32-27-generic/build M=/home/jesus/pruebas/c clea


```

And the error message after "make all":
```

make -C /lib/modules/2.6.32-27-generic/build M=/home/jesus/pruebas/c modules
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.32-27-generic'
make[2]: *** No hay ninguna regla para construir el objetivo `/home/jesus/pruebas/c/hello.c', necesario para `/home/jesus/pruebas/c/hello.o'.  Alto.
make[1]: *** [_module_/home/jesus/pruebas/c] Error 2
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.32-27-generic'
make: *** [all] Error 2


```

What am i doing wrong!! Many thanks!

---

### Post by johnl on 2011-01-05
What did you name your .c file?  It needs to be the same as the object file (hello.o) that you listed in your makefile, except it should end with .c (hello.c).

---

### Post by dwhitney67 on 2011-01-05
> **chuchi said:**
> 
What am i doing wrong!! Many thanks!

Follow johnl's advice with regards to naming your source file.

Also, simplify your Makefile with something like:
```

obj-m := hello.o        # Module Name is hello.c

KDIR  := /lib/modules/$(shell uname -r)/build

all:
        $(MAKE) -C $(KDIR) M=$(PWD) modules

clean:
        $(MAKE) -C $(KDIR) M=$(PWD) clean

```

---

### Post by chuchi on 2011-01-05
Ey!! now it works!!! My file name was already hello.c, but with your Makefile now it works. Many thanks to all!!!

---

