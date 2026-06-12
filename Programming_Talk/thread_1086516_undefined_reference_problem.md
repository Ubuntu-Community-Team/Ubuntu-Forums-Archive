---
title: "undefined reference problem"
date: 2009-03-04
forum: Programming Talk
---

### Post by veda87 on 2009-03-04
I have defined a simple function (print) in /usr/src/...../fs/ext2/print_value.c  and i am calling this function in /usr/src/...../fs/buffer.c 
```
void print_value(int num) {
      printk("the count is %d\n", num);
}
EXPORT_SYMBOL(print_value);

```

But when i run make, it shows the following error:```
fs/built-in.o: In function `__block_commit_write':
/usr/src/linux-2.6-kgdb.git/fs/buffer.c:1947: undefined reference to `print_value'

```

i have already included print_value.h file in buffer.c.

why am i getting this error and how to solve it.....

---

### Post by dwhitney67 on 2009-03-04
I do not know how you are building your modules; you did not list your Makefile.

But here's an example that includes two modules and a Makefile, followed by the instructions to load the modules...


MyPrintString.h:
```

#ifndef MY_PRINT_STRING_H
#define MY_PRINT_STRING_H

void print_string(const char* str);

#endif

```

MyPrintString.c:
```

#include <linux/module.h>
#include "MyPrintString.h"

#define DRIVER_AUTHOR "dwhitney67"
#define DRIVER_DESC   "A specialized print-string kernel module."

MODULE_LICENSE("GPL");
MODULE_AUTHOR(DRIVER_AUTHOR);            /* Who wrote this module? */
MODULE_DESCRIPTION(DRIVER_DESC);         /* What does this module do */


void print_string(const char* str)
{
  printk(str);
}
EXPORT_SYMBOL(print_string);

```

HelloWorld.c:
```

#include <linux/module.h>      // Needed by all modules
#include "MyPrintString.h"

#define DRIVER_AUTHOR "dwhitney67"
#define DRIVER_DESC   "A Hello World kernel module."

MODULE_LICENSE("GPL");
MODULE_AUTHOR(DRIVER_AUTHOR);            /* Who wrote this module? */
MODULE_DESCRIPTION(DRIVER_DESC);         /* What does this module do */


static int __init hello_world( void )
{
  print_string("hello world\n");
  return 0;
}

static void __exit goodbye_world( void )
{
  print_string("goodbye world\n");
}

module_init( hello_world );
module_exit( goodbye_world );

```

Makefile:
```

SRCS   = HelloWorld.c MyPrintString.c
OBJS   = $(SRCS:.c=.o)

obj-m += $(OBJS)

EXTRA_CFLAGS = -O2


all:
        $(MAKE) -C /lib/modules/`uname -r`/build M=$(PWD) modules

clean:
        $(MAKE) -C /lib/modules/`uname -r`/build M=$(PWD) clean
        $(RM) Module.markers modules.order

```

To build and then load modules:
```

make
sudo insmod ./MyPrintString.ko
sudo insmod ./HelloWorld.ko
sudo rmmod HelloWorld
sudo rmmod MyPrintString

```

I hope this helps.

---

