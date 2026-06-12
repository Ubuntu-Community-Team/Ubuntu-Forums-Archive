---
title: "How to compile a kernel module with openSSL?"
date: 2007-08-09
forum: Programming Talk
---

### Post by Spippo on 2007-08-09
Hi,

I'm making a kernel module for ubuntu. One of the functions in the module calculates a hash-value of a message. To do this, I want to use OpenSSL. When I compile my module, I always get the following error:

**openssl/ripemd.h: No such file or directory**

I know I installed openssl correct, because I can make normal application with it.
I think I'm missing something in the Makefile:

```

UNAME := $(shell uname -r)
KERNEL26 := 2.6
KERNELVERSION := $(findstring $(KERNEL26),$(UNAME))
SSLFLAG	= `pkg-config openssl --cflags`
SSLLIBS	= `pkg-config openssl --libs`

all:: user

ifeq ($(KERNELVERSION),2.6)

obj-m	:= skeleton.o

INCLUDE	:= -I/usr/include/asm/mach-default/ -I/usr/include/
KDIR	:= /lib/modules/$(shell uname -r)/build
PWD		:= $(shell pwd)

all::
	$(MAKE)  $(SSLFLAG) $(SSLLIBS) -C $(KDIR) $(INCLUDE) SUBDIRS=$(PWD) modules
	
else

TARGET	:= skeleton
INCLUDE	:= -I/lib/modules/`uname -r`/build/include -I/usr/include/asm/mach-default/ -I/usr/include/
CFLAGS	:= -O2 -Wall -DMODULE -D__KERNEL__ -DLINUX
CC	:= gcc

all:: ${TARGET}.o

${TARGET}.o: ${TARGET}.c
	$(CC) $(SSLFLAG) $(SSLLIBS) $(CFLAGS) ${INCLUDE} -c ${TARGET}.c
	
endif

user: user.c
	gcc -o $@ $<

```

Also, if I have two files (Vertex.h and Vertex.c) which contain a structure and some function for this structure, how can I include this into the module?

Thanks

---

### Post by Spippo on 2007-08-09
OK, I found how to add multiple files:

```

obj-m	:= mymodule.o
mymodule-objs := skeleton.o Vertex.o

```

But now I still need to know how to include openSSL

Anyone an idea?

Thanks

---

