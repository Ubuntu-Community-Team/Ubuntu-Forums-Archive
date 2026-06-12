---
title: "stuck at compilation of kernel module."
date: 2012-08-28
forum: Packaging and Compiling Programs
---

### Post by gmmo1971 on 2012-08-28
Hi, I am trying to build the hello world module described in this article

[http://tldp.org/LDP/lkmpg/2.6/html/lkmpg.html#AEN121](http://tldp.org/LDP/lkmpg/2.6/html/lkmpg.html#AEN121)

and I using the exact makefile and source described but it does not compile. I am somewhat new to linux so troubleshooting this is not easy for me.

the make file looks like this: (and I have tabs there)

obj-m += hello-1.o

all:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

but when I issue make, I get this:


gustavo@gustavo-Null:~/Desktop/projects/kernel_mod$ make
make -C /lib/modules/3.2.0-29-generic-pae/build M=/home/gustavo/Desktop/projects/kernel_mod modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-29-generic-pae'
scripts/Makefile.build:44: /home/gustavo/Desktop/projects/kernel_mod/Makefile: No such file or directory
make[2]: *** No rule to make target `/home/gustavo/Desktop/projects/kernel_mod/Makefile'.  Stop.
make[1]: *** [_module_/home/gustavo/Desktop/projects/kernel_mod] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-29-generic-pae'
make: *** [all] Error 2
gustavo@gustavo-Null:~/Desktop/projects/kernel_mod$ 


this makefile is somewhat magic to me.

Any help I great appreciate.

thx!

---

### Post by sanderj on 2012-08-28
Does that directory exist? Check with:

```
ll /lib/modules/`uname -r`/build
```

(note the ` ... left of your "1"-key)

And:

Why are you using a 2.6 instruction?
Compiling a kernel and kernel modules is not easy. As you're new to Linux and this is your first post, I would advice you to do some easier things first

---

### Post by gmmo1971 on 2012-08-28
the directory definitely exists.


root@gustavo-Null:/home/gustavo/Desktop/projects/kernel_mod# ll /lib/modules/`uname -r`/build
lrwxrwxrwx 1 root root 43 Jul 27 11:38 /lib/modules/3.2.0-29-generic-pae/build -> /usr/src/linux-headers-3.2.0-29-generic-pae/
root@gustavo-Null:/home/gustavo/Desktop/projects/kernel_mod# 


I don't want to build regular code, I need to build kernel code. This I need to figure out how this is compiled properly.

Anyone knows how to spell out the exact gcc or g++ command to compile the code, instead of using the misterious makefile?

thx,

---

### Post by sanderj on 2012-08-28
I have no problems compiling. See below.

So:

> /home/gustavo/Desktop/projects/kernel_mod/Makefile: No such file or directory

Does the file 'Makefile' exist in your directory. With a capital M?


```
sander@R540:~/kul/kernel$ vi Makefile
sander@R540:~/kul/kernel$ vi hello-1.c
sander@R540:~/kul/kernel$ make
make -C /lib/modules/3.2.0-29-generic/build M=/home/sander/kul/kernel modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-29-generic'
  CC [M]  /home/sander/kul/kernel/hello-1.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/sander/kul/kernel/hello-1.mod.o
  LD [M]  /home/sander/kul/kernel/hello-1.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-29-generic'
sander@R540:~/kul/kernel$ 
sander@R540:~/kul/kernel$ ll
total 100
drwxrwxr-x  3 sander sander  4096 Aug 28 15:07 ./
drwxr-xr-x 12 sander sander  4096 Aug 28 15:06 ../
-rw-rw-r--  1 sander sander   392 Aug 28 15:07 hello-1.c
-rw-rw-r--  1 sander sander  3497 Aug 28 15:07 hello-1.ko
-rw-rw-r--  1 sander sander   253 Aug 28 15:07 .hello-1.ko.cmd
-rw-rw-r--  1 sander sander   690 Aug 28 15:07 hello-1.mod.c
-rw-rw-r--  1 sander sander  2568 Aug 28 15:07 hello-1.mod.o
-rw-rw-r--  1 sander sander 25265 Aug 28 15:07 .hello-1.mod.o.cmd
-rw-rw-r--  1 sander sander  2496 Aug 28 15:07 hello-1.o
-rw-rw-r--  1 sander sander 25162 Aug 28 15:07 .hello-1.o.cmd
-rw-rw-r--  1 sander sander   158 Aug 28 15:07 Makefile
-rw-rw-r--  1 sander sander    42 Aug 28 15:07 modules.order
-rw-rw-r--  1 sander sander     0 Aug 28 15:07 Module.symvers
drwxrwxr-x  2 sander sander  4096 Aug 28 15:07 .tmp_versions/
sander@R540:~/kul/kernel$

```

---

### Post by gmmo1971 on 2012-08-28
What version of linux are you using?

---

### Post by sanderj on 2012-08-28
> **gmmo1971 said:**
> What version of linux are you using?

Can you first post the output of

```
ll /home/gustavo/Desktop/projects/kernel_mod/

```
to answer my question?

---

### Post by gmmo1971 on 2012-08-28
sanderj, you were correct. My makefile was misspelled all lower case. Plus I also had to compile as superuser otherwise it would not work.

the fix was to become superuser and access root

sudo su -

then rename the makefile to Makefile.

thx!

P.S. This is why I prefer windows. Linux has too many little details to know before you can actually do something.

---

