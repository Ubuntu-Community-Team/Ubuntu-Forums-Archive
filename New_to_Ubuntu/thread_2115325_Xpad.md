---
title: "Xpad"
date: 2013-02-12
forum: New to Ubuntu
---

### Post by Stainlessflesh on 2013-02-12
Hi,

I'm very new to Linux, I only installed yesterday. Everything has been going smoothly but I wanted to install the drivers so I can use my Xbox controller with Skyrim.

I've followed the steps on [https://help.ubuntu.com/community/Xbox360Controller](https://help.ubuntu.com/community/Xbox360Controller) and when I got to the "Creating the Makefile" I started having problems.

I made the "Makefile", went to the terminal, typed mkdir xpad and then typed make. After which I received this error:

> USER@USER-IMEDIA-2426:~/xpad$ make
make modules -C /usr/src/linux-headers-3.5.0-23-generic SUBDIRS=/home/USER/xpad
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-23-generic'
  CC [M]  /home/USER/xpad/xpad.o
/home/USER/xpad/xpad.c:66:28: fatal error: linux/smp_lock.h: No such file or directory
compilation terminated.
make[2]: *** [/home/USER/xpad/xpad.o] Error 1
make[1]: *** [_module_/home/USER/xpad] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-23-generic'
make: *** [all] Error 2

My "Makefile" looks like this:

[IMG]http://i48.tinypic.com/mv41ly.jpg[/IMG]

Any help would be appreciated, thanks ):P

---

### Post by Sealbhach on 2013-02-12
Hi, have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=1916412"), where somebody recently was trying the same thing. Seems you don't have to compile any more.

.

---

### Post by Stainlessflesh on 2013-02-12
Thanks alot! I'll have a look now and try it out, hopefully it'll get sorted out :)

---

