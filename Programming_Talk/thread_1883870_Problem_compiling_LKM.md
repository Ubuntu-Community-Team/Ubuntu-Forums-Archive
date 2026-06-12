---
title: "Problem compiling LKM"
date: 2011-11-20
forum: Programming Talk
---

### Post by piyush.kansalx on 2011-11-20
Hi,

I am facing error while trying to build a LKM under Ubuntu 11.04 which is running as a guest OS under VirtualBox.

Following are the details:

piyush@piyush-VirtualBox:~/SomePath$ ll
-rw-r--r-- 1 piyush piyush  2570 2011-11-20 03:32 hello.c
-rw-r--r-- 1 piyush piyush   163 2011-11-20 04:01 Makefile

piyush@piyush-VirtualBox:~/SomePath$ cat Makefile 
```
obj-m := hello.o

all:
    make &#8722;C /lib/modules/2.6.38-12-generic/build M=$(PWD) modules
clean:
    make &#8722;C /lib/modules/2.6.38-12-generic/build M=$(PWD) clean

```piyush@piyush-VirtualBox:~/SomePath$ make
make &#8722;C /lib/modules/2.6.38-12-generic/build M=/home/piyush/SomePath modules
make[1]: Entering directory `/home/piyush/SomePath'
make[1]: *** No rule to make target `&#8722;C'.  Stop.
make[1]: Leaving directory `/home/piyush/SomePath'
make: *** [all] Error 2

Please suggest.

---

