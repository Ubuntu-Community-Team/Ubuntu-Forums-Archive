---
title: "insmod: Unknown symbol in module"
date: 2009-12-21
forum: Programming Talk
---

### Post by volodymyr on 2009-12-21
Hello everyone!

I am trying to make two kernel modules which uses each other functions. My problem is that I got modules properly compiled, but the symbol is not resolved for one of them.

To make things simple, let's call these modules as m1 and m2. 

m2 is exporting function void func_m2(void). The m1 is calling this function. Both modules properly compiles.

After it all compiles I need to load first the m2 module (because it has exported func_m2 function) and afterwards m1 module. So, let's make it:

```
volodymyr@sv1:~/development/kmodules/m2$ sudo insmod ./m2.ko
```Now, lets load m1 module which is trying to use func_m2:

```
volodymyr@sv1:~/development/kmodules/m1$ sudo insmod ./m1.ko
insmod: error inserting './m1.ko': -1 Unknown symbol in module
```Following is what I see in logs:

```
volodymyr@sv1:~/development/kmodules/m1$ dmesg | tail
[ 3938.166616] Loading m2 module ...
[ 3963.078055] m1: no symbol version for func_m2
[ 3963.078059] m1: Unknown symbol func_m2
```So, it seems like the refercens to symbol func_m2 is not resolved. Interesting. Let's check if it is present in symbol table:

```
volodymyr@sv1:~/development/kmodules$ cat /proc/kallsyms | grep 'func_m2'
ffffffffa00530d0 r __ksymtab_func_m2    [m2]
ffffffffa00530e8 r __kstrtab_func_m2    [m2]
ffffffffa00530e0 r __kcrctab_func_m2    [m2]
ffffffffa0053000 T func_m2      [m2]
000000004edd543f a __crc_func_m2        [m2]
```As you can see, the func_m2 is actually present in symbol table. So why m1 can't be loaded? 

I have installed properly linux headers for my kernel and linux sources. I did not make any modifications in kernel, it is untouched, and it's version is: 2.6.31-16-generic (I run x64)

Now, to show you full picture I am putting here the source code and Makefile I used for this test for both m1 and m2 modules.

m1 module:

m1.c:

```
#include <linux/module.h>
#include <linux/kernel.h>

extern void func_m2(void);

int hello_start(void)
{
        printk(KERN_INFO "Loading m1 module ...\n");

        func_m2();

        return 0;
}

void hello_end(void)
{
        printk(KERN_INFO "Unloading m1 ...\n");
}

module_init(hello_start);
module_exit(hello_end);

MODULE_LICENSE("GPL");
```Makefile:

```
obj-m := m1.o

all:
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean
```m2 module:

m2.c:

```
#include <linux/module.h>
#include <linux/kernel.h>

int hello_start(void)
{
        printk(KERN_INFO "Loading m2 module ...\n");

        return 0;
}

void hello_end(void)
{
        printk(KERN_INFO "Unloading m2 ...\n");
}

void func_m2(void)
{
        printk(KERN_INFO "This a function in m2\n");
}

module_init(hello_start);
module_exit(hello_end);

MODULE_LICENSE("GPL");
EXPORT_SYMBOL(func_m2);
```Makefile:

```
obj-m := m2.o
export-objs := m2.o

all:
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean
```

---

### Post by dwhitney67 on 2009-12-21
Here are some issues I found with your code (after doing some research)...

1.  Your initialization and termination functions should be declared static and properly identified.  For example, in m1.c:
```

...

**static** int **__init** hello_start(void)
{
        printk(KERN_INFO "Loading m1 module ...\n");

        func_m2();

        return 0;
}

**static** void **__exit** hello_end(void)
{
        printk(KERN_INFO "Unloading m1 ...\n");
}

...

```
Repeat this for m2.c.


2.  Build both of your modules together, using the same Makefile.  I bet if you look closely at the output from your existing Makefile for m1.c, you will see a warning indicating that func_m2() is undefined.  Anyhow, the consolidated Makefile should look like:
```

SRCS   = m1.c m2.c
OBJS   = $(SRCS:.c=.o)

obj-m += $(OBJS)

EXTRA_CFLAGS = -O2


all:
        $(MAKE) -C /lib/modules/`uname -r`/build M=$(PWD) modules

clean:
        $(MAKE) -C /lib/modules/`uname -r`/build M=$(PWD) clean
        $(RM) Module.markers modules.order

```
After both modules are built, run insmod on 'm2.ko' before issuing the insmod for 'm1.ko'.  Check results via dmesg.

---

### Post by volodymyr on 2009-12-21
[dwhitney67]("http://ubuntuforums.org/member.php?u=322753"),

Thank you very much for your help. You saved hours of my time :) Compiling both modules in one make file works, thanks!

However I need the projects to be separated in a different directories. Putting them into one directory in one makefile is messy ... How can I build each module independently? I can make one makefile which accesses N directories and builds their source files ... but I want to avoid that ...

Thank you for your help!

P.S. Changing function prototype to static did not changed much, it is more for optiomization I guess.

---

### Post by volodymyr on 2009-12-21
In particular, I have the following structure:

m1 folder contains 2 c files, 

m2 folder contains 3 c files

I can't use your makefile as it generates *.ko per each c file ...

---

### Post by dwhitney67 on 2009-12-21
Sorry to reply back so late...

I did little research and found a way to build modules in separate directories.  The example I used is much simpler than what you have, but perhaps it is adaptable.

I have following manifest of files in a directory called 'ExportSymbol'...
```

$ ls -CFR
.:
include/  Makefile  mod1/  mod2/

./include:
m2_func.h

./mod1:
Makefile  module1.c

./mod2:
Makefile  module2.c

```

The m2_func.h appears as:
```

#ifndef M2_FUNC_H
#define M2_FUNC_H

void m2_func(void);

#endif

```

The top-level Makefile appears as:
```

obj-y := mod1/ mod2/

all:
        $(MAKE) -C /lib/modules/`uname -r`/build M=$(PWD) modules

clean:
        $(MAKE) -C /lib/modules/`uname -r`/build M=$(PWD) clean
        $(RM) Module.markers modules.order

```

The Makefile and module1.c, which are in mod1/, appear as:
```

SRCS   = module1.c
OBJS   = $(SRCS:.c=.o)

obj-m += $(OBJS)

EXTRA_CFLAGS += -I${PWD}/include

all:
        $(MAKE) -C /lib/modules/`uname -r`/build M=$(PWD) modules

clean:
        $(MAKE) -C /lib/modules/`uname -r`/build M=$(PWD) clean
        $(RM) Module.markers modules.order

```
```

#include "m2_func.h"
#include <linux/module.h>
#include <linux/kernel.h>

static int __init hello_start(void)
{
   printk(KERN_INFO "Loading m1 module ...\n");

   m2_func();

   return 0;
}

static void __exit hello_end(void)
{
   printk(KERN_INFO "Unloading m1 ...\n");
}

module_init(hello_start);
module_exit(hello_end);

MODULE_LICENSE("GPL");

```
The Makefile and module2.c, which are in mod2/, appear as:
```

SRCS   = module2.c
OBJS   = $(SRCS:.c=.o)

obj-m += $(OBJS)

EXTRA_CFLAGS += -I${PWD}/include

all:
        $(MAKE) -C /lib/modules/`uname -r`/build M=$(PWD) modules

clean:
        $(MAKE) -C /lib/modules/`uname -r`/build M=$(PWD) clean
        $(RM) Module.markers modules.order

```
```

#include "m2_func.h"
#include <linux/module.h>
#include <linux/kernel.h>

static int __init hello_start(void)
{
   printk(KERN_INFO "Loading m2 module ...\n");

   return 0;
}

static void __exit hello_end(void)
{
   printk(KERN_INFO "Unloading m2 ...\n");
}

void m2_func(void)
{
   printk(KERN_INFO "This a function in m2\n");
}

module_init(hello_start);
module_exit(hello_end);

MODULE_LICENSE("GPL");
EXPORT_SYMBOL(m2_func);

```

I've attached the code above in a tar-ball in case you want to copy the source code to your system in a convenient manner.


P.S.
> 
I can't use your makefile as it generates *.ko per each c file ...

Ummm... the Makefile is doing its job.  A 'ko' file is a kernel object file; you will have one for each .c source file.  There's no way around this.  If you do not want multiple ko-files, then put all of your code in one source file.

---

### Post by volodymyr on 2009-12-22
Hello dwhitney67,

Thank you very much for your help. I am playing with the example of a new Makefile.

> **dwhitney67 said:**
> 
P.S.

Ummm... the Makefile is doing its job.  A 'ko' file is a kernel object file; you will have one for each .c source file.  There's no way around this.  If you do not want multiple ko-files, then put all of your code in one source file.

Well, in my previous Makefile for multiple c files I got only one ko file. The makefile which links all object files into one ko is the following:

```
obj-m := maindriver.o
maindriver-objs := m1.o m2.o m3.o m4.o m5.0

all:
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean
```

As you can see, this makefile generates only one ko file: maindriver.ko which consist from m1.c, m2.c, m3.c, m4.c, m5.c source files ...

I will try to combine both type of makefiles into one and will see what happen. 

Thanks for your help, you gave me a right direction to solve the problem.

---

### Post by dwhitney67 on 2009-12-22
> **volodymyr said:**
> 
Well, in my previous Makefile for multiple c files I got only one ko file. The makefile which links all object files into one ko is the following:

```
obj-m := maindriver.o
maindriver-objs := m1.o m2.o m3.o m4.o m5.0

all:
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean
```

As you can see, this makefile generates only one ko file: maindriver.ko which consist from m1.c, m2.c, m3.c, m4.c, m5.c source files ...

I was not aware of this feature; I need to give it a shot myself.

Thanks for correcting me.

---

### Post by volodymyr on 2009-12-22
It's working pretty fine for me, basically it links all objects generated from *.c files into one main *ko, i.e. like in Windows :)

---

### Post by volodymyr on 2009-12-22
So I confirm that I was able to solve the problem with a mixture of mine and dwhitney67 Makefiles.

I just added EXTRA_CFLAGS += -I${PWD}/include to mine Makefile which uses multiple *.c files to generate one *.ko file . It now compiles and runs perfectly!

Thank you!

---

### Post by hallowwar on 2010-04-04
&#38750;&#24120;&#22909;&#65292;&#23398;&#20064;&#12290;

---

