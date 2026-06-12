---
title: "installing lua failure"
date: 2013-04-27
forum: New to Ubuntu
---

### Post by Hobo4bob on 2013-04-27
slashdot@slashdot-SN68S:~/lua-5.2.2$ make linux test
cd src && make linux
make[1]: Entering directory `/home/slashdot/lua-5.2.2/src'
make all SYSCFLAGS="-DLUA_USE_LINUX" SYSLIBS="-Wl,-E -ldl -lreadline"
make[2]: Entering directory `/home/slashdot/lua-5.2.2/src'
gcc -O2 -Wall -DLUA_COMPAT_ALL -DLUA_USE_LINUX    -c -o lua.o lua.c
lua.c:67:31: fatal error: readline/readline.h: No such file or directory
compilation terminated.
make[2]: *** [lua.o] Error 1
make[2]: Leaving directory `/home/slashdot/lua-5.2.2/src'
make[1]: *** [linux] Error 2
make[1]: Leaving directory `/home/slashdot/lua-5.2.2/src'
make: *** [linux] Error 2

i need help installing lua i already have installed ncurses if you ask i'm running ubuntu 12.04 so far i have kept getting this error any ideas plz

---

### Post by DuckHook on 2013-04-28
Hi and welcome to the forums and to Ubuntu.

This being your first posting, and to Absolute Beginners, I assume that you are new to Ubuntu and probably to Linux. In the Linux distro universe there is absolutely no reason for new users to go outside of the repositories for their apps. This is just one of many bad Windows habits that it is important to break. Otherwise, you are inviting security nightmares.

To install LUA, it is only necessary to search for it in Synaptic and install. Since it is easier for us to help using the command line, just do:```
sudo apt-get update && sudo apt-get install lua5.1
```We are invoking apt to first update your sources, and then install LUA 5.1. There are later versions, but they are not officially supported by Ubuntu 12.04 and you should not install them unless they have functionality that you cannot do without. Once you get better versed in Linux, that is the time to do more complicated things, but compiling from source for new users is just bad news.

<edit>

BTW, if you prefer using Synaptic, it is not installed by default in Ubuntu (a bad decision in my opinion, but it is what it is). To install it, do:```
sudo apt-get update && sudo apt-get install synaptic
```</edit>

---

