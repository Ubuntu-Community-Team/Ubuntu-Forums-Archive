---
title: "writing a device driver trouble"
date: 2008-08-24
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-08-24
I followed the directions at this [_[COLOR="Blue"]site[/COLOR]_]("http://www.freesoftwaremagazine.com/articles/drivers_linux?page=0%2C1")

And it didn't work??
I have ubuntu fiesty

I tried this but since their isn't a "/usr/src/kernel-source-2.6.8" i changed it to "/usr/src/linux-headers-2.6.20-17"

The hardest part for me is getting the first example to compile. If you show me that then i could easily start making drivers (basic of course)

I have done about 5 tutorials and none worked so If you could write a single example step by step (not assuming anything) and it works then ill be good

Please test, and assume im a moron (im not:))

---

### Post by jinksys on 2008-08-24
What errors are you getting? 

Also, make sure you have build-essential installed.

---

### Post by Mr.Macdonald on 2008-08-24
this is the output of (in directory ~/Program/C/Drive)

make -C /usr/src/linux-headers-2.6.20-17 M=pwd modules
```
make: Entering directory `/usr/src/linux-headers-2.6.20-17'

  WARNING: Symbol version dump /usr/src/linux-headers-2.6.20-17/Module.symvers
           is missing; modules will have no dependencies and modversions.

scripts/Makefile.build:17: /usr/src/linux-headers-2.6.20-17/pwd/Makefile: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-headers-2.6.20-17/pwd/Makefile'.  Stop.
make: *** [_module_pwd] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.20-17'

```

Here is some potentially useful info
```
aidan@aidan:~/Program/C/Drivers$ ls
Makefile  nothing.c
aidan@aidan:~/Program/C/Drivers$ cat Makefile 
obj-m := nothing.o
aidan@aidan:~/Program/C/Drivers$ cat nothing.c 
#include <linux/module.h>

MODULE_LICENSE("Dual BSD/GPL");
aidan@aidan:~/Program/C/Drivers$ 

```

---

### Post by jinksys on 2008-08-24
Ok, you are using a badly written tutorial.

This is a better tutorial, 

[http://www.tldp.org/LDP/lkmpg/2.6/html/index.html](http://www.tldp.org/LDP/lkmpg/2.6/html/index.html)

The tutorial you are using says to run this command...

make -C /usr/src/linux-headers-2.6.20-17 M=pwd modules

it should be 

make -C /usr/src/linux-headers-2.6.20-17 M=`pwd` modules

It would be better to start with a better tutorial,  

I'd read [THIS](http://ubuntuforums.org/showthread.php?t=800251) thread, focusing on the posts by dwhitney67, and then hop over to the tutorial I posted here.

Good Luck.

---

### Post by dwhitney67 on 2008-08-24
Actually, the Make command should be:
```
make -C /lib/modules/`uname -r`/build M=$PWD modules
```
Note that *nix system store their headers in different locations, depending on the distro.  Using the format above, you are guaranteed to obtain the headers because 'build' is a link to where the actual headers reside.

P.S.  I used $PWD above in lieu of pwd in case you were to create a Makefile.  For instance:
```
obj-m += nothing.o

EXTRA_CFLAGS = -O2

all:
        $(MAKE) -C /lib/modules/`uname -r`/build M=$(PWD) modules

clean:
        $(MAKE) -C /lib/modules/`uname -r`/build M=$(PWD) clean
        $(RM) Module.markers modules.order
```

---

### Post by amo-ej1 on 2008-08-25
The de facto standard book for learning how to write device drivers is Linux Device Drivers (currently 3rd edition, fully adapted to the 2.6 kernel) and it's freely available at [http://lwn.net/Kernel/LDD3/](http://lwn.net/Kernel/LDD3/) it begins with touching the problems you're encountering.

---

