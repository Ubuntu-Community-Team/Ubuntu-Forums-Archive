---
title: "Building the simple module fails. -No rule to make target `&#8722;C'. Stop"
date: 2011-10-29
forum: Programming Talk
---

### Post by ksuneel on 2011-10-29
Registered: May 2005
Posts: 7

Rep: 
Building the simple module fails. -No rule to make target `&#8722;C'. Stop
Here is my sample Hello world program.

****************Hello.c**************

#define MODULE
#include<linux/module.h>
#include<linux/kernel.h>


int init_module(void) {
printk("<1> Hello World \n"); 
return 0;
}

void cleanup_module(void)
{
printk("<1> Goodbuy World \n"); 
}

make file for that.

*********************Makefile***************************

obj&#8722;m:=hello.o

all:
make &#8722;C /lib/modules/$(shell uname -r)/build M=$(pwd) modules
clean:
make &#8722;C /lib/modules/$(shell uname -r)/build M=$(pwd) clean

When I do make This is what I see. 


make &#8722;C /lib/modules/3.0.0-12-generic/build M= modules
make[1]: Entering directory `/home/suneel/Samples'
make[1]: *** No rule to make target `&#8722;C'. Stop.
make[1]: Leaving directory `/home/suneel/Samples'
make: *** [all] Error 2


Please suggest some solution.

---

### Post by trent.josephsen on 2011-10-29
I suggest using a text editor, and not something that transforms a simple hyphen into a [Unicode minus sign](http://www.fileformat.info/info/unicode/char/2212/index.htm).

---

### Post by ksuneel on 2011-10-30
Thank you very much for the answer. That's amazing catch. That fixed the problem. But still build was not successful 

This is what I see in the build output

> make[1]: leaving directory /usr/src/linux-headers.....
Building modules stage 2. 
MODPOST 0 modules.

Any suggestion?

---

### Post by ksuneel on 2011-10-30
I have retyped the whole make file again.Some Unicode characters are causing the problem. It works after retyping same thing in gedit. Thank you very much for your support.

---

