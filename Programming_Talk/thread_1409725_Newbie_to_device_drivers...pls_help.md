---
title: "Newbie to device drivers...pls help"
date: 2010-02-17
forum: Programming Talk
---

### Post by aaroon on 2010-02-17
Hi

i am currently learning to write device drivers, i started with a tutorial from freesoftwaremagazine.com and i tried to write a hello.c program. but i am unable to compile it.
this is my hello.c code
[PHP]
#include <linux/init.h>
#include <linux/module.h>
#include <linux/kernel.h>

MODULE_LICENSE("Dual BSD/GPL");

static int hello_init(void) {
  printk("<1> Hello world!\n");
  return 0;
}
static void hello_exit(void) {
  printk("<1> Bye, cruel world\n");
}

module_init(hello_init);
module_exit(hello_exit);
[/PHP]

Makefile

[PHP]
obj-m := hello.o 
KDIR  := /lib/modules/$(shell uname -r)/build
PWD   := $(shell pwd)
default:
	$(MAKE) -C $(KDIR) M=$(PWD) modules
[/PHP]

when i try to make in the folder where i have written my hello.c it give me an error like this

[PHP]make -C /lib/modules/2.6.31-19-generic/build M=/home/arun/Desktop/driver prog modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-19-generic'
make[1]: *** No rule to make target `prog'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-19-generic'
make: *** [default] Error 2
[/PHP]

i checked up this prob..and also found that i have linux headers for my kernel in src directory. and i dunno if i have installed them. should do i do some configure or make in the headers folder to set it up.


what am i going wrong...pls help

---

### Post by cariboo on 2010-02-18
You should get better help here.

---

### Post by falconindy on 2010-02-18
Don't specify 'prog' in your make command, as you haven't defined that as a target in your Makefile. In reality, as long as you're compiling for the kernel you currently have booted on, simply running 'make' without any arguments should be sufficient.

---

### Post by aaroon on 2010-02-18
thanks...it worked...actually i was doing only make...but i made a stupid mistake..the directory was "driver prog"...then i changed it "driverprog"...think giving space was the problem....

---

### Post by dwhitney67 on 2010-02-18
EDIT:  Ignore my post; it appears that you resolved the issue.


@ the OP

The word "prog" that you provided in the following statement does not correlate with the information that you provided in the Makefile.
```

make -C /lib/modules/2.6.31-19-generic/build M=/home/arun/Desktop/driver **prog** modules 

```
Did you run make with one Makefile, and then post another???  Anyhow, the Makefile you have posted should work fine; that is, providing that your source file has a name of 'hello.c', that you have the kernel header files installed, and the 'build-essential' package installed.


P.S.  In the source file, the include statements for <linux/init.h> and <linux/kernel.h> are not necessary for the basic module you have created.

---

