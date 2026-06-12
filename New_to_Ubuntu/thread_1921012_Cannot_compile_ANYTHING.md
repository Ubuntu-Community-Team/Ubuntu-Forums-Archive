---
title: "Cannot compile ANYTHING"
date: 2012-02-05
forum: New to Ubuntu
---

### Post by Rtedmonston on 2012-02-05
[LEFT]I'm still new to this process, and I've posted about it before but got nowhere. Yes, I do need to compile some things, I'm trying to compile aircrack, bitcoin, openSSL and a few others, and I always get errors. I've been trying to follow this guide to a T': 

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

but I usually get tripped up because of dependencies aren't met, some missing file, or there's no ./config command and no way to make one. 

for instance I'm trying to compile aircrack, instructions say: make/make install, that's it, however I get: 

[quote=russell@aser.aspire-7740]russell@russell-Aspire-7740:~/src/aircrack-ng-1.1$ make
make -C src all
make[1]: Entering directory `/home/russell/src/aircrack-ng-1.1/src'
make -C osdep
make[2]: Entering directory `/home/russell/src/aircrack-ng-1.1/src/osdep'
Building for Linux
make[3]: Entering directory `/home/russell/src/aircrack-ng-1.1/src/osdep'
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -fPIC -I..    -c -o linux.o linux.c
linux.c: In function ‘is_ndiswrapper’:
linux.c:165:17: error: variable ‘unused’ set but not used [-Werror=unused-but-set-variable]
linux.c: In function ‘linux_set_rate’:
linux.c:334:22: error: variable ‘unused’ set but not used [-Werror=unused-but-set-variable]
linux.c: In function ‘linux_set_channel’:
linux.c:807:22: error: variable ‘unused’ set but not used [-Werror=unused-but-set-variable]
linux.c: In function ‘linux_set_freq’:
linux.c:896:22: error: variable ‘unused’ set but not used [-Werror=unused-but-set-variable]
linux.c: In function ‘set_monitor’:
linux.c:1022:22: error: variable ‘unused’ set but not used [-Werror=unused-but-set-variable]
linux.c: In function ‘do_linux_open’:
linux.c:1366:12: error: variable ‘unused_str’ set but not used [-Werror=unused-but-set-variable]
linux.c:1352:15: error: variable ‘unused’ set but not used [-Werror=unused-but-set-variable]
linux.c: In function ‘get_battery_state’:
linux.c:1982:35: error: variable ‘current’ set but not used [-Werror=unused-but-set-variable]
cc1: all warnings being treated as errors

make[3]: *** [linux.o] Error 1
make[3]: Leaving directory `/home/russell/src/aircrack-ng-1.1/src/osdep'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/russell/src/aircrack-ng-1.1/src/osdep'
make[1]: *** [osd] Error 2
make[1]: Leaving directory `/home/russell/src/aircrack-ng-1.1/src'
make: *** [all] Error 2[/quote]

Where I was getting missing openssl files before, I notice the "warnings being treated as errors" signal, is there an option to turn that off? It doesn't come with a ./config script and autogen.sh doesn't do anything to create one (I have autoconf installed). What am I doing wrong? Am I missing something? Seems like the majority of these problems are something missing, when I look for that it too needs something else which needs something else which needs this which needs that and blah blah blah until I end up on a wild goose chase hunting down packages/software and I have no idea what for :confused:. 

Is there an easier way to do this?
[/LEFT]

---

### Post by cariboo on 2012-02-05
Aircrack-ng is broken, has no debian maintainer, and as of Precise, no longer in the repositories. If you want to play with aircrack-ng, I'd suggest you use [BackTrack]("http://www.backtrack-linux.org/"), and use their forum for support, as we don't support it here. Thread closed.

If you need help with compiling a progrm, please use something else.

---

