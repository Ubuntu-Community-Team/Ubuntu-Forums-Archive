---
title: "Help compiling a module"
date: 2006-09-03
forum: Programming Talk
---

### Post by bcw on 2006-09-03
Hello,

Kubuntu Dapper on a Fujitsu Stylistic ST5032D.  This computer has several buttons around the display for input, and a fellow has written a kernel module to use them in GNU/Linux.  I compiled them from his tar file successfully before.

Now, I've reinstalled my system after a series of wild experiments, and I can't compile the package.  I have recompiled kernels in the past, and this package, but I'm a Java programmer by profession, and haven't spent a lot of time with the GNU C tool chain recently.  I'm perhaps a bit ahead of the 'trained monkey' stage.

Here is the output:
```
root@aphrodite:~/incoming/tablet/ST5032D/fjbtndrv-1.1# ls -l /usr/src
total 43424
lrwxrwxrwx  1 root src        27 2006-09-04 10:37 linux -> linux-headers-2.6.15-26-686
drwxr-xr-x 19 root root     4096 2006-09-03 21:56 linux-headers-2.6.15-26
drwxr-xr-x  5 root root     4096 2006-09-04 10:46 linux-headers-2.6.15-26-686
lrwxrwxrwx  1 root src        19 2006-09-03 21:09 linux-OLDVERSION.1157337441 -> linux-source-2.6.15
drwxr-xr-x 21 root root     4096 2006-09-04 10:48 linux-source-2.6.15
-rw-r--r--  1 root root 44403157 2006-08-03 13:02 linux-source-2.6.15.tar.bz2
root@aphrodite:~/incoming/tablet/ST5032D/fjbtndrv-1.1# ls -l
total 16
-rw-r--r-- 1 bret bret 7125 2006-03-17 22:35 fjbuttons.c
-rw-r--r-- 1 bret bret  285 2006-09-04 11:28 Makefile
root@aphrodite:~/incoming/tablet/ST5032D/fjbtndrv-1.1# cat Makefile
obj-m += fjbtndrv.o

fjbtndrv-objs := fjbuttons.o

#ifneq ($(__KERNEL__),)
#endif


default:
        @make -C /lib/modules/`uname -r`/build M=`pwd` modules

install:
        @make -C /lib/modules/`uname -r`/build M=`pwd` modules_install

clean:
        @make -C /lib/modules/`uname -r`/build M=`pwd` clean
root@aphrodite:~/incoming/tablet/ST5032D/fjbtndrv-1.1# make
make[1]: Entering directory `/lib/modules/2.6.15-26-686/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.15-26-686/build'
make: *** [default] Error 2
root@aphrodite:~/incoming/tablet/ST5032D/fjbtndrv-1.1#
```

I hope it's something simple I just don't know yet.  Please ask for any information you need I haven't provided.

Thanks,
Bret

---

