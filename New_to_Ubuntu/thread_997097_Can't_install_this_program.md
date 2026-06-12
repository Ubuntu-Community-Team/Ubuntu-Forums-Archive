---
title: "Can't install this program"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by Vorac on 2008-11-29
Help. All day I'm trying to install this, and all I manage to do is get a Different kind of error every time :confused:. So:

s613n7157@adski-desktop:~$ cd /home/s613n7157/Garbage/parted-1.8.8
s613n7157@adski-desktop:~/Garbage/parted-1.8.8$ ./configure --without-readline
...
config.status: creating po/Makefile

Type 'make' to compile parted.
s613n7157@adski-desktop:~/Garbage/parted-1.8.8$ make
...
```
Making all in reiserfs
make[3]: Entering directory `/home/s613n7157/Garbage/parted-1.8.8/libparted/fs/reiserfs'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/s613n7157/Garbage/parted-1.8.8/libparted/fs/reiserfs'
make[3]: Entering directory `/home/s613n7157/Garbage/parted-1.8.8/libparted/fs'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/s613n7157/Garbage/parted-1.8.8/libparted/fs'
make[2]: Leaving directory `/home/s613n7157/Garbage/parted-1.8.8/libparted/fs'
Making all in .
make[2]: Entering directory `/home/s613n7157/Garbage/parted-1.8.8/libparted'
Makefile:575: warning: overriding commands for target `linux.lo'
Makefile:568: warning: ignoring old commands for target `linux.lo'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -std=gnu99  -I. -I../lib -I../lib -I../include     -g -O2 -Werror -MT libparted.lo -MD -MP -MF .deps/libparted.Tpo -c -o libparted.lo libparted.c
 gcc -std=gnu99 -I. -I../lib -I../lib -I../include -g -O2 -Werror -MT libparted.lo -MD -MP -MF .deps/libparted.Tpo -c libparted.c  -fPIC -DPIC -o .libs/libparted.o
 gcc -std=gnu99 -I. -I../lib -I../lib -I../include -g -O2 -Werror -MT libparted.lo -MD -MP -MF .deps/libparted.Tpo -c libparted.c -o libparted.o >/dev/null 2>&1
mv -f .deps/libparted.Tpo .deps/libparted.Plo
/bin/bash ../libtool --tag=CC   --mode=compile gcc -std=gnu99  -I. -I../lib -I../lib -I../include     -g -O2 -Werror -MT natmath.lo -MD -MP -MF .deps/natmath.Tpo -c -o natmath.lo `test -f 'cs/natmath.c' || echo './'`cs/natmath.c
 gcc -std=gnu99 -I. -I../lib -I../lib -I../include -g -O2 -Werror -MT natmath.lo -MD -MP -MF .deps/natmath.Tpo -c cs/natmath.c  -fPIC -DPIC -o .libs/natmath.o
cc1: warnings being treated as errors
cs/natmath.c:79: warning: C99 inline functions are not supported; using GNU89
cs/natmath.c:79: warning: to disable this warning use -fgnu89-inline or the gnu_inline function attribute
cs/natmath.c:85: warning: C99 inline functions are not supported; using GNU89
make[2]: *** [natmath.lo] Error 1
make[2]: Leaving directory `/home/s613n7157/Garbage/parted-1.8.8/libparted'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/s613n7157/Garbage/parted-1.8.8/libparted'
make: *** [all-recursive] Error 1
s613n7157@adski-desktop:~/Garbage/parted-1.8.8$ 

```
And the thing i'm trying to install is this [http://www.gnu.org/software/parted/index.shtm](http://www.gnu.org/software/parted/index.shtm) ; because I want to farmat the other hard disc.

---

### Post by cdtech on 2008-11-29
You have a partition editor located at "System > Administration > Parition editor".

---

### Post by gandaran on 2008-11-29
> **cdtech said:**
> You have a partition editor located at "System > Administration > Parition editor".

only if you install gparted (gnome) or qtparted (kde) in synaptic!

---

### Post by Vorac on 2008-11-29
10x a lot :) Let's now see hol long does it take to format a 1,5T drive :)

---

### Post by Vorac on 2008-11-29
Bad news (for me). gparted sais:
"A partition cannot have a length of -1 sectors"

,which, google says is due to it's inability to cope with larger than a 1000GB partitions. :(

---

### Post by echo.whoami on 2008-11-29
What if you make 2-3 partitions and then format each. Well not the best advise but that's all i can think.

---

