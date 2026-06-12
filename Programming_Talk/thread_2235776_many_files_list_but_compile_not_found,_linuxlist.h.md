---
title: "many files list but compile not found, linux/list.h: No such file or directory"
date: 2014-07-22
forum: Programming Talk
---

### Post by zerop2 on 2014-07-22
sudo apt-get install linux-headers-$(uname -r)

already installed and the newest one

i am using ubuntu 12.04 and then i download ubuntu 14 have the same error too

i add full path of all missing header file in hello.c and finally have poison.h not found, can not be solved any more

i search for the error, then find a makefile below

```
all:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
```

however after make, return nothing to be done for 'all'

then i change to

```
obj-m += hello.o

hello.o:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean
```


it result in another error

```
wonder@wonder-VirtualBox:~/layer$ make
cc    -c -o hello.o hello.c
In file included from hello.c:3:0:
/usr/src/linux-headers-3.8.0-29-generic/include/linux/module.h:9:24: fatal error: linux/list.h: No such file or directory
compilation terminated.
make: *** [hello.o] Error 1
```

i use the make file in old version of oreilly book linux device driver

it can make to run, however got error

it use cc, but not gcc, is it modules programming can only use cc, not gcc?

```
make: *** No rule to make target `cli_init.o', needed by `cli.o'.  Stop.
wonder@wonder-VirtualBox:~/layer$ make
cc -D__KERNEL__ -DMODULE -O -Wall -I/usr/src/linux-headers-3.8.0-29-generic/include   -c -o cli.o cli.c
cli.c:1:0: warning: "MODULE" redefined [enabled by default]
<command-line>:0:0: note: this is the location of the previous definition
In file included from /usr/src/linux-headers-3.8.0-29-generic/include/linux/kernel.h:6:0,
                 from /usr/src/linux-headers-3.8.0-29-generic/include/linux/cache.h:4,
                 from /usr/src/linux-headers-3.8.0-29-generic/include/linux/time.h:4,
                 from /usr/src/linux-headers-3.8.0-29-generic/include/linux/stat.h:18,
                 from /usr/src/linux-headers-3.8.0-29-generic/include/linux/module.h:10,
                 from cli.c:2:
/usr/src/linux-headers-3.8.0-29-generic/include/linux/linkage.h:5:25: fatal error: asm/linkage.h: No such file or directory
compilation terminated.
make: *** [cli.o] Error 1
wonder@wonder-VirtualBox:~/layer$ 

```
Makefile:

```
INCLUDEDIR = /usr/src/linux-headers-3.8.0-29-generic/include

CFLAGS = -D__KERNEL__ -DMODULE -O -Wall -I$(INCLUDEDIR)


OBJS = cli.o


all: $(OBJS)

install:
    install -d /lib/modules/$(VER)/misc /lib/modules/misc
    install -c cli.o /lib/modules/$(VER)/misc
    install -c cli.o /lib/modules/misc

clean:
    rm -f *.o *~ core
```

---

