---
title: "python linking to dl and other libs failed"
date: 2012-05-04
forum: Programming Talk
---

### Post by jxj988 on 2012-05-04
hello, 
i trying to build a gem5 simulator with python v2.7.3 and on  the final linking stage i get the following error 

/usr/local/lib/libpython2.7.a(dynload_shlib.o): In function `_PyImport_GetDynLoadFunc':
/usr/local/src/Apps/Python-2.7.3/Python/dynload_shlib.c:94: undefined reference to `dlsym'
/usr/local/src/Apps/Python-2.7.3/Python/dynload_shlib.c:130: undefined reference to `dlopen'
/usr/local/src/Apps/Python-2.7.3/Python/dynload_shlib.c:141: undefined reference to `dlsym'
/usr/local/src/Apps/Python-2.7.3/Python/dynload_shlib.c:133: undefined reference to `dlerror'
/usr/local/lib/libpython2.7.a(posixmodule.o): In function `posix_openpty':
/usr/local/src/Apps/Python-2.7.3/./Modules/posixmodule.c:3756: undefined reference to `openpty'
/usr/local/lib/libpython2.7.a(posixmodule.o): In function `posix_forkpty':
/usr/local/src/Apps/Python-2.7.3/./Modules/posixmodule.c:3816: undefined reference to `forkpty'


i'm using a scons to build the simulator and i can't change the signals to the gcc to include -ldl library and etc..

i've also tried to change the PATH to look in the python dir first without any luck.

any idea on how to fix this ? 

additional info : 
x64 PC ubuntu 64 -12.04 
python2.7.3

---

### Post by jaishank on 2012-09-17
Hey buddy, I am facing the same problem. Did you solve this problem btw? please help.

---

### Post by EmreJ on 2012-10-03
I had the same problem with EPD. I solved it by adding the flags **-ldl -lutil** to the linker.

---

