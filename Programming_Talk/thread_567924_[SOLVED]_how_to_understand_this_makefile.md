---
title: "[SOLVED] how to understand this makefile"
date: 2007-10-05
forum: Programming Talk
---

### Post by fyplinux on 2007-10-05
Hi, I am a novice on make, I dont really understand the following code of a makefile, hope you can explain for me.

the code comes from <The Linux Kernel Module Programming Guide 2.6.x>, links at [http://tldp.org/LDP/lkmpg/2.6/html/x181.html]("http://tldp.org/LDP/lkmpg/2.6/html/x181.html")

```
obj-m += hello.o

all:
   make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
   make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean
```

thanks.

---

### Post by dwhitney67 on 2007-10-05
```
obj-m += hello.o

all:
   make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
   make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean
```
The first line is appending the 'hello.o' object file to the list of obj-m(odules).  From the Makefile listing you provided, it does not appear that obj-m is used.

The 'all' entry is the first (and the default) entry point of this Makefile.  It calls another Makefile located in /lib/modules/<your kernel version>/build, and passes that Makefile the args M (which is set equal to the present working directory you are in) and 'modules' (which is the entry point in the Makefile being called).

The 'clean' portion is very similar to the 'all' entry point, with the exception that 'clean' is being called.

You can verify the output of these commands to better understand what is taking place:

[FONT="Courier New"]$ uname -r
$ echo $PWD[/FONT]

---

