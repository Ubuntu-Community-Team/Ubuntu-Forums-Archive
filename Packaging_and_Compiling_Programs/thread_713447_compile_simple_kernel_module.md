---
title: "compile simple kernel module"
date: 2008-03-02
forum: Packaging and Compiling Programs
---

### Post by depressed77 on 2008-03-02
Hi all, 
please help me!

I have spent all the day trying to compile the example of chapter 2 of Linux Device Driver

#include <linux/init.h>
#include <linux/module.h>
static int hello_init(void)
{printk(KERN_ALERT "Hello");return 0;}
static int hello_exit(void)
{printk(KERN_ALERT "Bye");return 0;}
module_init(hello_init);
module_exit(hello_exit);

and stored it in hello.c. I also created a file called "makefile" with 
obj-m := hello.o

My uname -r is 2.6.22-14-generic
I have the following headers installed
linux-headers-2.6.22-14-generic (2.6.22.14.46)
I therefore entered
sudo make -C /usr/src/linux-headers-2.6.22-14-generic m="pwd" modules

and I get

make: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
make[1]: *** No rule to make target `arch/i386/kernel/asm-offsets.c', needed by `arch/i386/kernel/asm-offsets.s'.  Stop.
make: *** [prepare0] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'

In fact
/usr/src/linux-headers-2.6.22-14-generic/arch/i386/kernel$ dir
acpi  asm-offsets.s  cpu  Makefile

Where am I wrong? I am starting feeling really depressed about all these stuffs...
Thank you for any help/question that could help find a solution,
Paolo

---

### Post by dalonso on 2008-03-09
Hi, depressed77

unarchive the attachment. It's a kind of template you could use for other modules. It's not mine, I copied it also ;-) from r5u870 sources when I wanted to compile the udf module out of the kernel tree.

1) Copy hello.c to src/ (I already did it for you)
2) cd to src and edit Makefile (I already did it for you too): 

[LIST]Add, space separated, every *.o file to be linked against your module main linker object in the something-objs variable. In this example there's only hello.o, but you could have several *.c files each one being compiled to the corresponding *.o file linked together to form only 1 o file that in turn will become your *.ko. So you could end with something like:
[/LIST]

[INDENT]```
something-objs := src1.o src2.o src3.o
```
And in this actual example:
```
hello-objs := hello.o
```[/INDENT]

But in this case, because of being only one linker object, you should comment the hello-objs line!!!

[LIST]The resulting o file after linking together the previous something-objs files is going to be something.o. Put it into obj-m += something.o. In this example "something" being "hello"
[/LIST]

[INDENT]```
obj-m	+= something.o
```
And in this actual example:
```
obj-m += hello.o
```[/INDENT]

3) cd .., and simply "make" without arguments.

---

### Post by depressed77 on 2008-03-29
Hi Dalonso, 
sorry for my late reply.
Thank you very very much for your help :)

Paolo

---

### Post by dalonso on 2008-03-30
You are wellcome.

---

