---
title: "How to debug a Makefile"
date: 2007-02-26
forum: Programming Talk
---

### Post by 25an on 2007-02-26
Hi!
I am trying to compile the boot loader u-boot for a embedded system with arm.
The error that I get is

25an@25an-desktop:/opt/x-compile/eldk/workingarea/u-boot-1.1.5_atmel_1.2$ make CROSS_COMPILE=arm-linux- ARCH=arm

cc1: error: invalid option 'apcs-32'
hello_world.c:1: error: bad value (arm926ejs) for -mtune= switch

I have not managed to solve this, so now I have to "debug" the makefile.
I have tried to use echo but I dont understand the rules for were I can echo and not in the Makefile.
For example in the main Makefile I would like to print out the ALL
How can I do that?

ALL = $(obj)u-boot.srec $(obj)u-boot.bin $(obj)System.map $(U_BOOT_NAND)

all:		@echo $(ALL)

this dose not work.

any help is appreciated. Thanks

---

### Post by Arndt on 2007-02-26
> **25an said:**
> Hi!
I am trying to compile the boot loader u-boot for a embedded system with arm.
The error that I get is

25an@25an-desktop:/opt/x-compile/eldk/workingarea/u-boot-1.1.5_atmel_1.2$ make CROSS_COMPILE=arm-linux- ARCH=arm

cc1: error: invalid option 'apcs-32'
hello_world.c:1: error: bad value (arm926ejs) for -mtune= switch

I have not managed to solve this, so now I have to "debug" the makefile.
I have tried to use echo but I dont understand the rules for were I can echo and not in the Makefile.
For example in the main Makefile I would like to print out the ALL
How can I do that?

ALL = $(obj)u-boot.srec $(obj)u-boot.bin $(obj)System.map $(U_BOOT_NAND)

all:		@echo $(ALL)

this dose not work.

any help is appreciated. Thanks

I think you want the command on the next line. What comes directly after the colon is the dependencies.

```
all:		
              @echo $(ALL)
```

Look at the various options to 'make' too.

---

### Post by 25an on 2007-02-27
ALL = $(obj)u-boot.srec $(obj)u-boot.bin $(obj)System.map $(U_BOOT_NAND)

all:            $(ALL)

$(obj)u-boot.hex:       $(obj)u-boot
                $(OBJCOPY) ${OBJCFLAGS} -O ihex $< $@

$(obj)u-boot.srec:      $(obj)u-boot
                @echo $(OBJCOPY)
                $(OBJCOPY) ${OBJCFLAGS} -O srec $< $@

$(obj)u-boot.bin:       $(obj)u-boot
                $(OBJCOPY) ${OBJCFLAGS} -O binary $< $@

what I would like to do is to print something at the target all: 
so that I know if I reach it or not.

For example 

all:
          @echo "I have reach this far"
          $(ALL)

---

### Post by Arndt on 2007-02-27
> **25an said:**
> ALL = $(obj)u-boot.srec $(obj)u-boot.bin $(obj)System.map $(U_BOOT_NAND)

all:            $(ALL)

$(obj)u-boot.hex:       $(obj)u-boot
                $(OBJCOPY) ${OBJCFLAGS} -O ihex $< $@

$(obj)u-boot.srec:      $(obj)u-boot
                @echo $(OBJCOPY)
                $(OBJCOPY) ${OBJCFLAGS} -O srec $< $@

$(obj)u-boot.bin:       $(obj)u-boot
                $(OBJCOPY) ${OBJCFLAGS} -O binary $< $@

what I would like to do is to print something at the target all: 
so that I know if I reach it or not.

For example 

all:
          @echo "I have reach this far"
          $(ALL)

Yes, then "make all" ought to do the echo call. Doesn't it? But you shouldn't move the dependencies down from line they were on.

---

### Post by akshata on 2008-09-14
Hi, 
    I have typed the following C program
test.c
#include <linux/module.h> /* Needed by all modules */
#include <linux/kernel.h> /* Needed for KERN_INFO */
int init_module(void)
{
printk(KERN_INFO "Hello world 1.\n");
/*
* A non 0 return means init_module failed; module can't be loaded.
*/
return 0;
}
void cleanup_module(void)
{
printk(KERN_INFO "Goodbye world 1.\n");
}

the Makefile for test.c looks like this

obj&#8722;m += hello&#8722;1.o
all:
make &#8722;C /lib/modules/$(shell uname &#8722;r)/build M=$(PWD) modules
clean:
make &#8722;C /lib/modules/$(shell uname &#8722;r)/build M=$(PWD) clean

when i run a make in the same directory i get an error
make : Nothing to be done for 'all'. 

The test.ko file isnt being created.

Could anyone please tell me what the problem is and how to rectify it?

Thanks,
Akshata

---

