---
title: "Problems with compiling first program"
date: 2011-02-23
forum: Programming Talk
---

### Post by puruharsh on 2011-02-23
Hi,

I am currently using Ubuntu Ultimate Edition. I tried one of the examples in Linux Kernel Module Programming Guide, infact the very first one.

But when I gave a make command, I got the following error. Hope you can help me out with this.

root@bd-2147-linux:~/MyPrograms# make all
make -C /lib/modules/2.6.32-21-generic/build M=/home/pcs/MyPrograms modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
make[2]: *** No rule to make target `/home/pcs/MyPrograms/helloworld.c', needed by `/home/pcs/MyPrograms/helloworld.o'.  Stop.
make[1]: *** [_module_/home/pcs/MyPrograms] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make: *** [all] Error 2

My Make file contents are:

obj-m := helloworld.o

all:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
clean:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

Please let me know where the mistake lies,

Thanks in advance,
Harsha

---

### Post by cariboo on 2011-02-23
a bump for the move.

---

### Post by jbiggs12 on 2011-02-24
Does helloworld.o actually exist? From the looks of things make can't find it.

Edit: whoops, my bad. You need to compile the code first before you run it. Make sure your makefile compiles the sourcefile before running it.

---

### Post by cgroza on 2011-02-24
A make file just for helloworld? A line with gcc( C ) or g++ (C++) would work better.

---

### Post by johnl on 2011-02-25
Your makefile is correct for building a kernel module.  Likely you did not name your source file what it expects.

Your source file should be named helloworld.c in /home/pcs/MyPrograms/

Otherwise, if your source file is named foobar.c, change the first line of your makefile to:

```

obj-m := foobar.o

```

---

