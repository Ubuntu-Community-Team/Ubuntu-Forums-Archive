---
title: "Linux Headers pathes?"
date: 2011-02-23
forum: Programming Talk
---

### Post by ganga0 on 2011-02-23
Hello. I am not new to Ubuntu, but i got stuck a little bit.

I'm writting a loadable kernel module. And I wonder how to compile it. Each FAQ i've read says that i should just compile it like this:
> gcc -c -Wall hello_kernel.c
and then use some makefile, but it doesn't matter for now...

the problem is gcc do not have include paths needed so i get:
> hello_kernel.c:1: fatal error: linux/init.h: No such file or directory
compilation terminated.


i've tried this:
> gcc -c -Wall -I /usr/src/linux-headers-2.6.35-25/include/ hello_kernel.c

But it gives much more "no such file...".

So how can i get and set all include paths needed to compile a module?

---

### Post by johnl on 2011-02-23
Assuming your source file is called hello_kernel.c, try the following makefile:

```

obj-m := hello_kernel.o

all:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

```

You will need to make sure your kernel headers are installed (sudo apt-get install linux-headers-generic) prior to this.

Assuming everything is set up correctly, you should see something like:

```

user@host:~/Projects/hello_mod$ make
make -C /lib/modules/2.6.35-25-generic/build M=/home/user/Projects/hello_mod modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-25-generic'
  CC [M]  /home/user/Projects/hello_mod/hello.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/user/Projects/hello_mod/hello.mod.o
  LD [M]  /home/user/Projects/hello_mod/hello.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-25-generic'


```

From there you can load your module with 'insmode ./hello_kernel.ko'

---

