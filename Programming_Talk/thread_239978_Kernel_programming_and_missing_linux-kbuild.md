---
title: "Kernel programming and missing linux-kbuild"
date: 2006-08-20
forum: Programming Talk
---

### Post by bonefry on 2006-08-20
I started to learn how to write kernel modules.

So, I started to write a simple "Hello World" module, and tried to compile it.
My documentation says to create a Makefile with the line ...

obj-m += hello-1.o

I then tried to run "make" and an error occured, saying the syntax is not recognized.
I started to look at my own documentation and I found out that I need "kbuild" installed.

But the package, linux-kbuild, which is included in Debian, is missing from Dapper.

What to do now ?
Do you know of an alternative way to build kernel modules ?

---

### Post by tseliot on 2006-08-20
Did you try this?
```
sudo apt-get install build-essential kernel-package
```

---

### Post by bonefry on 2006-08-20
eh, no, that didn't do it.
thanks anyway.

I solved it though ... a kernel recompilation was needed (only a compilation of the sources, as the newly compiled kernel doesn't need to be installed).

I also made a link in /lib/modules/`uname -r`/build to point to /usr/src/linux-source-2.6.15 (the sources I have).

And now the makefile looks like this:

obj-m += hello-1.o

all:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

And it worked.

---

