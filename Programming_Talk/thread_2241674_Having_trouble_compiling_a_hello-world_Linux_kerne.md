---
title: "Having trouble compiling a hello-world Linux kernel module"
date: 2014-08-27
forum: Programming Talk
---

### Post by s3a on 2014-08-27
I'm trying to compile a Linux kernel module called hello-2.c using the command "make -C /lib/modules/$(uname -r)/build M=${PWD} modules" (without the quotes) (which I found online), and the following is the (seemingly successful) output.:
```
make: Entering directory `/usr/src/linux-headers-3.2.0-4-amd64'
  Building modules, stage 2.
  MODPOST 0 modules
make: Leaving directory `/usr/src/linux-headers-3.2.0-4-amd64'
```

However, I don't see a hello-2.ko (in the same folder or anywhere else for that matter).

Everything I am doing is within a folder/directory called "thefolder" (without the quotes) in the "/tmp" directory (without the quotes).

Could someone please tell me why I can't see a hello-2.ko, and what to do to get it?

---

### Post by dwhitney67 on 2014-08-27
Your instructions do not indicate that you set obj-m to the name of the expected object file name.  Create a Makefile to simplify the process of building the module.  For additional info, read here:  [http://ubuntuforums.org/showthread.php?t=314596&p=8187295#post8187295](http://ubuntuforums.org/showthread.php?t=314596&p=8187295#post8187295)

P.S.  In your particular case, you should probably be using:
```

obj-m += hello-2.o

...

```

---

### Post by s3a on 2014-08-27
> **dwhitney67 said:**
> Your instructions do not indicate that you set obj-m to the name of the expected object file name.  Create a Makefile to simplify the process of building the module.  For additional info, read here:  [http://ubuntuforums.org/showthread.php?t=314596&p=8187295#post8187295](http://ubuntuforums.org/showthread.php?t=314596&p=8187295#post8187295)

P.S.  In your particular case, you should probably be using:
```

obj-m += hello-2.o

...

```
I don't know what I did differently, but using your Makefile syntax worked. Thanks!

Having said that, though, why doesn't "obj-m += hello-2.ko" (without the quotes) work (instead of "obj-m += hello-2.o" - without the quotes)?:
```
obj-m += hello-2.o # Why doesn't "obj-m += hello-2.ko" (without the quotes) work?

all:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean
```

I ask, since I thought that the .ko file extension became the successor of the .o file extension.

Also, could you please elaborate about what that Makefile syntax does (specifically)?

---

### Post by dwhitney67 on 2014-08-27
I would imaging that the .o (regular object file) is an intermediate product that is produced before the kernel module (.ko) file is produced.

As for Makefiles, in a nutshell, it is a collection of zero or more declarations (e.g. obj-m), and then 'rules' (e.g. all and clean) that can be invoked using the command make, followed by the rule name.  If a rule name is not specified, then the first rule in the file is executed.  A Makefile can make one's life easier so that complicated commands do not have to repeatedly be entered on the command line.

For (a lot) more about Makefiles, read here:  [http://www.gnu.org/software/make/manual/make.html](http://www.gnu.org/software/make/manual/make.html)

---

### Post by s3a on 2014-08-29
> **dwhitney67 said:**
> I would imaging that the .o (regular object file) is an intermediate product that is produced before the kernel module (.ko) file is produced.

As for Makefiles, in a nutshell, it is a collection of zero or more declarations (e.g. obj-m), and then 'rules' (e.g. all and clean) that can be invoked using the command make, followed by the rule name.  If a rule name is not specified, then the first rule in the file is executed.  A Makefile can make one's life easier so that complicated commands do not have to repeatedly be entered on the command line.

For (a lot) more about Makefiles, read here:  [http://www.gnu.org/software/make/manual/make.html](http://www.gnu.org/software/make/manual/make.html)
Thanks again!

---

