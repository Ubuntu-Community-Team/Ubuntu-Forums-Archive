---
title: "Header file problem .."
date: 2013-02-08
forum: Programming Talk
---

### Post by prismctg on 2013-02-08
I m new in C , I found this error during compilation ```
trendchip.c:19:24: fatal error: linux/slab.h: No such file or directory

```..... How can I solve this ?where i find this header file ?

---

### Post by Bachstelze on 2013-02-08
Install the linux-headers package that corresponds to your kernel version.

---

### Post by prismctg on 2013-02-08
> **Bachstelze said:**
> Install the linux-headers package that corresponds to your kernel version.
I already did this..but same problem again

---

### Post by Bachstelze on 2013-02-08
Then you will need to provide additional information (and really, you should have done that in your first post!). Where does the code come from? How are you compiling it?

---

### Post by prismctg on 2013-02-09
Here is the code [http://pastebin.com/2ELRTqsV]("http://pastebin.com/2ELRTqsV")

i m using gcc 4.7

---

### Post by Bachstelze on 2013-02-09
By "how you are compiling it" I meant "which command are you running",of course...

---

### Post by prismctg on 2013-02-09
> **Bachstelze said:**
> By "how you are compiling it" I meant "which command are you running",of course...

```
gcc -o trendchip trendchip.c
```

---

### Post by Bachstelze on 2013-02-09
That's not how you compile kernel code, but you will have to Google how to do it or wait for someone else to answer because I am not a kernel expert myself.

---

### Post by Bachstelze on 2013-02-09
Or alternatively, look in the documentation. You probably did not obtain this code by itself.

---

### Post by xb12x on 2013-02-10
Try something like this, replacing the linux version with the one you have:

gcc -Wall -D__KERNEL__ -DMODULE -I/usr/src/linux-2.6.28-11-generic/include -O -g -I.. -c -o trendchip.o trendchip.c


Also, here is a generic Makefile.
Put Makefile in the source's directory and enter

make

```

# obj-m is a list of what kernel modules to build.  The .o and other
# objects will be automatically built from the corresponding .c file -
# no need to list the source files explicitly.

obj-m := trendchip.o 

# KDIR is the location of the kernel source.  The current standard is
# to link to the associated source tree from the directory containing
# the compiled modules.
KDIR  := /lib/modules/$(shell uname -r)/build

# PWD is the current working directory and the location of our module
# source files.
PWD   := $(shell pwd)

# default is the default make target.  The rule here says to run make
# with a working directory of the directory containing the kernel
# source and compile only the modules in the PWD (local) directory.
default:
	$(MAKE) -C $(KDIR) M=$(PWD) modules

clean:
	${MAKE} -C ${KDIR} M=${PWD} clean



```

---

