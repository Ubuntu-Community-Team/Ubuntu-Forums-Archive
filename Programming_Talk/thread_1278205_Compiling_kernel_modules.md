---
title: "Compiling kernel modules"
date: 2009-09-29
forum: Programming Talk
---

### Post by bluedalmatian on 2009-09-29
Im trying to build a simple kernel module to learn about device driver programing on 8.04 Hardy.

Ive tried installing the kernel header and kernel source packages but Im still getting errors at compile time about certain headers being missing.

Which packages do I need, what headers to i need for the -I option and do I need to link against a library?

Thanks
Andrew

---

### Post by dwhitney67 on 2009-09-29
You may already have all of the necessary kernel header files.  The issue you are having could be either 1) you are using an incorrect header file in your kernel module source code, or 2) you are not compiling the module correctly.

If you provide your module and a description of how you are building it, then it may be possible to help you overcome the hurdle.

Also, you may find your answer here: [http://lwn.net/Kernel/LDD3/](http://lwn.net/Kernel/LDD3/)
Specifically, examine Chapter 2.

---

### Post by bluedalmatian on 2009-10-01
Im doing

#include <linux/module.h>

#include <linux/kernel.h>

and then

gcc -D__KERNEL__ -I /usr/src/linux-headers-2.6.24-16/include/ -DMODULE -Wall -O2 -c mykmodule.c -o mykmodule.o

---

### Post by dwhitney67 on 2009-10-01
Did you have any success reading the Linux Kernel how-to site?

Personally, I would recommend that you utilize a Makefile in lieu of using the gcc command from the command line.

Try a Makefile like this:
```

SRCS   = mykmodule.c
OBJS   = $(SRCS:.c=.o)

obj-m += $(OBJS)

EXTRA_CFLAGS = -O2


all:
        $(MAKE) -C /lib/modules/`uname -r`/build M=$(PWD) modules

clean:
        $(MAKE) -C /lib/modules/`uname -r`/build M=$(PWD) clean
        $(RM) Module.markers modules.order

```

---

