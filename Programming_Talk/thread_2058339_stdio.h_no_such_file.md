---
title: "stdio.h no such file"
date: 2012-09-15
forum: Programming Talk
---

### Post by wxwx0104 on 2012-09-15
when i makefile a module. i meet this problem, no such file or  directory. it works if i use gcc -c. the o file appears.(i think i means  the code is right). I installed the build-essential. and the stdio.h is  in the direction usr/inculde/stdio.h(so the build-essential is already  installed). i do not know what is going on.
i tried 2 kind of Makefile both of them cannot work.
```
ifneq ($(KERNELRELEASE),)
    obj-m    := d.o

else
    KDIR    := /lib/modules/$(shell uname -r)/build
    PWD        := $(shell pwd)

    default:
    $(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules
    endif
``````

obj-m := hello.o
KERNELDIR ?= /usr/src/linux-source-3.2.0
PWD := $(shell pwd)

all:
    $(MAKE) -C $(KERNELDIR) M=$(PWD) modules

``````

#include <stdio.h>
#include <string.h>
#include <fcntl.h>
#include <errno.h>
#include <termios.h>
#include <unistd.h>
#include <xdo.h>
#include <X11/Xlib.h>
#include <X11/keysym.h>

```the h file i include.

I checked all the modules i can Makefile. the include usually like```
include <linux/*.h>
``` I think i make some mistakes in the include path. however i do not know how to change it.

---

### Post by trent.josephsen on 2012-09-15
Post the error message?

---

### Post by wxwx0104 on 2012-09-15
> **trent.josephsen said:**
> Post the error message?
```

[LIST=1]
[*]make -C /lib/modules/3.2.0-29-generic/build SUBDIRS=/media/SYSTEM/a modules
[*]make[1]: Entering directory `/usr/src/linux-headers-3.2.0-29-generic'
[*]  CC [M]  /media/SYSTEM/a/b.o
[*]/media/SYSTEM/a/b.c:1:23: fatal error: stdio.h: No such file or directory
[*]compilation terminated.
[*]make[2]: *** [/media/SYSTEM/a/b.o] Error 1
[*]make[1]: *** [_module_/media/SYSTEM/a] Error 2
[*]make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-29-generic'
[*]make: *** [default] Error 2
[/LIST]


```
I did install the bulid-essential and the rest of the h file i include

---

### Post by spjackson on 2012-09-15
> **wxwx0104 said:**
> ```

[LIST=1]
[*]/media/SYSTEM/a/b.c:1:23: fatal error: stdio.h: No such file or directory
[*]compilation terminated.
[/LIST]
 
```I did install the bulid-essential and the rest of the h file i include
There are lots of internet pages that explain this. [Here's one]("http://stackoverflow.com/questions/10345778/compiling-kernel-error-stdio-h-no-such-file-or-directory"). In essence, you cannot use a userspace library in a kernel module. libc is a userspace library. You can't find stdio.h because you shouldn't be using it.

---

### Post by wxwx0104 on 2012-09-16
> **spjackson said:**
> There are lots of internet pages that explain this. [Here's one]("http://stackoverflow.com/questions/10345778/compiling-kernel-error-stdio-h-no-such-file-or-directory"). In essence, you cannot use a userspace library in a kernel module. libc is a userspace library. You can't find stdio.h because you shouldn't be using it.
you mean I cannot use this. However, I need the last three h file to simulate the function of a keyboard. I use ```
gcc -c d.c
``` the d.o appears which cannot be insmod in the new ubuntu. Maybe i should change to a older version of linux?

---

### Post by spjackson on 2012-09-16
> **wxwx0104 said:**
> you mean I cannot use this. However, I need the last three h file to simulate the function of a keyboard. I use ```
gcc -c d.c
``` the d.o appears which cannot be insmod in the new ubuntu. Maybe i should change to a older version of linux?
I hadn't noticed that you were using X11 functions as well as stdio.h! If you can find an old kernel that depends on X, I'd be very much surprised.

I don't know how without doing the research, but I am sure that it is possible to simulate the function of a keyboard by writing a kernel module.  However, you can't write a kernel module with X11 functions. If you want to write your simulation with X11 functions, then I imagine you may be able to do that as some kind of plugin to X11 - I don't know whether it's possible or not.

---

