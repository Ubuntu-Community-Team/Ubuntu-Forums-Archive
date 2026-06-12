---
title: "my first module"
date: 2010-02-18
forum: Programming Talk
---

### Post by kernelnewbie1 on 2010-02-18
Hello friends,
 as every beginner i wrote my "hello world " module , it got compiled successfully, got inserted , even could be removed , but the problem was 

1) i had to do this as root , as there were compiling warnings (though it produced hello.ko) and also i could not insert module as a normal user

2)the output "hello world " and "good bye world" is not being printed on screen , if i use KERN_INFO in printk statement , these output can only be seen using dmesg or in /var/log/messages 
but if i use KERN_ALERT output is seen nowhere (screen or dmesg or in /var/log/messages )

what is the mistake in my program ?

** thanks in advance** to the helpful people of linux community , because i'm sure u will help me
==================================================================================================
the program i wrote is :: see #2

---

### Post by kernelnewbie1 on 2010-02-18
/ the program i wrote was
//hello.c
#include <linux/module.h>       /* Needed by all modules */
#include <linux/kernel.h>       /* Needed for KERN_INFO */
int init_module(void)
{
        printk(KERN_ALERT "Hello world 1.\n");
        /*
         * A non 0 return means init_module failed; module can't be loaded.
         */
        return 0;
}
void cleanup_module(void)
{
        printk(KERN_INFO "Goodbye world 1.\n");
}


//Makefile
obj-m := he.o 
KDIR  := /lib/modules/$(shell uname -r)/build
PWD   := $(shell pwd)
default:
  <tab> $(MAKE) -C $(KDIR) M=$(PWD) modules
clean:
   <tab>$(MAKE) -C $(KDIR) M=$(PWD) clean 

//compiling
#make
----------------
make -C /lib/modules/2.6.28-18-generic/build M=/home/newbie/lin/modules modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-18-generic'
  CC [M]  /home/newbie/lin/modules/he.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/newbie/lin/modules/he.mod.o
  LD [M]  /home/newbie/lin/modules/he.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-18-generic'

-----------------------
#insmod hello.ko  
# rmmod hello   // no output is seen but prompt is promptly returned !
# tail /var/log/messages
-----
// hello world not seen as i hav used KERN_ALERT
Feb 18 17:58:39 intel kernel: [ 3324.462330] Goodbye world 1.
-----
#dmesg | grep hello
---
 he: module license 'unspecified' taints kernel
// no printk statements here
---


///////// one more thing , whats the heck about this make file , if i give spaces instead of tab it makes a difference and give errors on compilation , is there any options to make makefile go easy on me !

---

### Post by Satoru-san on 2010-02-18
I&#12288;can almost gaurentee that you will not get an answer here.

Click the little report button on your post and ask the mod to move it to:

[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39) <-- programming forum.

---

### Post by falconindy on 2010-02-18
> **kernelnewbie1 said:**
> Hello friends,
 as every beginner i wrote my "hello world " module , it got compiled successfully, got inserted , even could be removed , but the problem was 

1) i had to do this as root , as there were compiling warnings (though it produced hello.ko) and also i could not insert module as a normal user
Working as intended. If you could insert modules as a regular user, this would pose a security risk. You can avoid having to be root for the compile itself by having your kernel headers somewhere that isn't owned by root.

> **kernelnewbie1 said:**
> 2)the output "hello world " and "good bye world" is not being printed on screen , if i use KERN_INFO in printk statement , these output can only be seen using dmesg or in /var/log/messages 
but if i use KERN_ALERT output is seen nowhere (screen or dmesg or in /var/log/messages )

what is the mistake in my program ?

** thanks in advance** to the helpful people of linux community , because i'm sure u will help me
==================================================================================================
the program i wrote is :: see #2
You'll need to dig through your system logger to determine where KERN_ALERT level messages are sent. I don't know enough about this to give you a definitive answer.

---

### Post by cariboo on 2010-02-18
You should get some help here.

---

