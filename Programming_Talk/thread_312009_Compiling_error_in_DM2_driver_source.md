---
title: "Compiling error in DM2 driver source"
date: 2006-12-03
forum: Programming Talk
---

### Post by Lucas2005 on 2006-12-03
Hello,

I'm quite new to ubuntu, but i messed with red hat about 3-4 years ago, lol

I resently installed ubuntu about a month ago, and i love it,  but i have only basic understanding of C++ (one class in college, 3 years ago).  so put things as easy as possible please.  I researched how to do this as much as i could, this is my first post.

I have a DM2 mixman controller, and i'm trying to figure out how to use it with Terminator X or so....

I found this:

[http://oregonstate.edu/~bonserp/blog/](http://oregonstate.edu/~bonserp/blog/)

I downloaded the file "dm2-0.1" from that post and tried to compile it.

I have this installed:
Ubuntu Linux 6.06 LTS Dapper Drake
linux-686-smp (Dual Core)
linux-headers-2.6.15-27
linux-headers-2.6.15-27-686
linux-image-686
linux-kernel-headers
linux-restricted-modules-2.6.15-27-686
linux-restricted-modules-686
linux-restricted-common
util-linux
build-essential

it's extracted in my home directory, The README says i should just run "make", but this is the output:

```
oscar@oscar-laptop:~/dm2-0.1$ make
make -C /lib/modules/2.6.15-27-686/build M=/home/oscar/dm2-0.1
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-27-686'
  CC [M]  /home/oscar/dm2-0.1/dm2.o
/home/oscar/dm2-0.1/dm2.c:24:29: error: linux/usb/input.h: No such file or directory
/home/oscar/dm2-0.1/dm2.c: In function ‘dm2_int’:
/home/oscar/dm2-0.1/dm2.c:119: warning: implicit declaration of function ‘input_regs’
/home/oscar/dm2-0.1/dm2.c:121: warning: implicit declaration of function ‘input_report_rel’
/home/oscar/dm2-0.1/dm2.c:121: error: ‘REL_X’ undeclared (first use in this function)
/home/oscar/dm2-0.1/dm2.c:121: error: (Each undeclared identifier is reported only once
/home/oscar/dm2-0.1/dm2.c:121: error: for each function it appears in.)
/home/oscar/dm2-0.1/dm2.c:122: error: ‘REL_Y’ undeclared (first use in this function)
/home/oscar/dm2-0.1/dm2.c:125: warning: implicit declaration of function ‘input_report_key’
/home/oscar/dm2-0.1/dm2.c:125: error: ‘BTN_LEFT’ undeclared (first use in this function)
/home/oscar/dm2-0.1/dm2.c:127: error: ‘BTN_MIDDLE’ undeclared (first use in this function)
/home/oscar/dm2-0.1/dm2.c:129: error: ‘BTN_RIGHT’ undeclared (first use in this function)
/home/oscar/dm2-0.1/dm2.c:131: warning: implicit declaration of function ‘input_sync’
/home/oscar/dm2-0.1/dm2.c:136: warning: implicit declaration of function ‘input_report_abs’
/home/oscar/dm2-0.1/dm2.c:136: error: ‘ABS_X’ undeclared (first use in this function)
/home/oscar/dm2-0.1/dm2.c:137: error: ‘ABS_Y’ undeclared (first use in this function)
/home/oscar/dm2-0.1/dm2.c:138: error: ‘ABS_Z’ undeclared (first use in this function)
/home/oscar/dm2-0.1/dm2.c: In function ‘store_config’:
/home/oscar/dm2-0.1/dm2.c:234: warning: unused variable ‘dm2_dev’
/home/oscar/dm2-0.1/dm2.c: In function ‘dm2_probe’:
/home/oscar/dm2-0.1/dm2.c:259: warning: implicit declaration of function ‘input_allocate_device’
/home/oscar/dm2-0.1/dm2.c:259: warning: assignment makes pointer from integer without a cast
/home/oscar/dm2-0.1/dm2.c:260: warning: assignment makes pointer from integer without a cast
/home/oscar/dm2-0.1/dm2.c:310: error: dereferencing pointer to incomplete type
/home/oscar/dm2-0.1/dm2.c:311: error: dereferencing pointer to incomplete type
/home/oscar/dm2-0.1/dm2.c:312: error: dereferencing pointer to incomplete type
/home/oscar/dm2-0.1/dm2.c:312: error: dereferencing pointer to incomplete type
/home/oscar/dm2-0.1/dm2.c:313: warning: implicit declaration of function ‘usb_to_input_id’
/home/oscar/dm2-0.1/dm2.c:313: error: dereferencing pointer to incomplete type
/home/oscar/dm2-0.1/dm2.c:314: error: dereferencing pointer to incomplete type
/home/oscar/dm2-0.1/dm2.c:315: error: dereferencing pointer to incomplete type
/home/oscar/dm2-0.1/dm2.c:315: error: dereferencing pointer to incomplete type
/home/oscar/dm2-0.1/dm2.c:316: error: dereferencing pointer to incomplete type
/home/oscar/dm2-0.1/dm2.c:316: error: dereferencing pointer to incomplete type
/home/oscar/dm2-0.1/dm2.c:318: error: dereferencing pointer to incomplete type
/home/oscar/dm2-0.1/dm2.c:318: warning: implicit declaration of function ‘BIT’
/home/oscar/dm2-0.1/dm2.c:318: error: ‘EV_KEY’ undeclared (first use in this function)
/home/oscar/dm2-0.1/dm2.c:318: error: ‘EV_REL’ undeclared (first use in this function)
/home/oscar/dm2-0.1/dm2.c:319: error: dereferencing pointer to incomplete type
/home/oscar/dm2-0.1/dm2.c:319: error: ‘REL_X’ undeclared (first use in this function)
/home/oscar/dm2-0.1/dm2.c:319: error: ‘REL_Y’ undeclared (first use in this function)
/home/oscar/dm2-0.1/dm2.c:320: error: dereferencing pointer to incomplete type
/home/oscar/dm2-0.1/dm2.c:320: warning: implicit declaration of function ‘LONG’
/home/oscar/dm2-0.1/dm2.c:320: error: ‘BTN_MOUSE’ undeclared (first use in this function)
/home/oscar/dm2-0.1/dm2.c:320: error: ‘BTN_LEFT’ undeclared (first use in this function)
/home/oscar/dm2-0.1/dm2.c:320: error: ‘BTN_RIGHT’ undeclared (first use in this function)
/home/oscar/dm2-0.1/dm2.c:321: error: ‘BTN_MIDDLE’ undeclared (first use in this function)
/home/oscar/dm2-0.1/dm2.c:321: error: ‘BTN_SIDE’ undeclared (first use in this function)
/home/oscar/dm2-0.1/dm2.c:323: error: dereferencing pointer to incomplete type
/home/oscar/dm2-0.1/dm2.c:323: error: ‘EV_ABS’ undeclared (first use in this function)
/home/oscar/dm2-0.1/dm2.c:324: error: dereferencing pointer to incomplete type
/home/oscar/dm2-0.1/dm2.c:324: error: ‘ABS_X’ undeclared (first use in this function)
/home/oscar/dm2-0.1/dm2.c:324: error: ‘ABS_Y’ undeclared (first use in this function)
/home/oscar/dm2-0.1/dm2.c:324: error: ‘ABS_Z’ undeclared (first use in this function)
/home/oscar/dm2-0.1/dm2.c:326: warning: implicit declaration of function ‘input_register_device’
/home/oscar/dm2-0.1/dm2.c:352: warning: implicit declaration of function ‘input_unregister_device’
/home/oscar/dm2-0.1/dm2.c:358: warning: implicit declaration of function ‘input_free_device’
make[2]: *** [/home/oscar/dm2-0.1/dm2.o] Error 1
make[1]: *** [_module_/home/oscar/dm2-0.1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-27-686'
make: *** [all] Error 2
oscar@oscar-laptop:~/dm2-0.1$
oscar@oscar-laptop:~/dm2-0.1$ sudo make install
make: *** No rule to make target `install'.  Stop.
oscar@oscar-laptop:~/dm2-0.1$
```


I'm I doing something wrong? I'll email the author later on,

Thanks in advance for the help  :)

---

### Post by Lucas2005 on 2006-12-06
Anybody??

---

### Post by Lucas2005 on 2006-12-06
The author responded in his blog,

i had to change this line in the dm2.c file

#include <linux/usb/input.h>    to    #include <linux/usb_input.h>

because of my kernel, it now compiles and works as a mouse

---

