---
title: "ctype.h error during driver compile"
date: 2007-01-11
forum: Programming Talk
---

### Post by computergroove on 2007-01-11
I am trying to compile a driver for an elo touch screen and I get to the make command and I get:

user@user-desktop:/home/elocontrol$ make
make -C /lib/modules/2.6.15-27-386/build SUBDIRS=/home/elocontrol modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-27-386'
  CC [M]  /home/elocontrol/main.o
In file included from /home/elocontrol/main.c:10:
/home/elocontrol/elocontrol.h:12:19: error: ctype.h: No such file or directory
make[2]: *** [/home/elocontrol/main.o] Error 1
make[1]: *** [_module_/home/elocontrol] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-27-386'
make: *** [default] Error 2

What do I need to do to add the ctype.h library to my compiler? Thanks

---

### Post by slavik on 2007-01-11
try doing 'sudo apt-get isntall build-essential' if you haven't

---

