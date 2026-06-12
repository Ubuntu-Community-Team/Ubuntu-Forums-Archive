---
title: "Building wg/wrk. used wget, unzip, make, I can see the green file, wont execute?"
date: 2013-02-23
forum: New to Ubuntu
---

### Post by xekon on 2013-02-23
running ubuntu 12.10

I am trying to build wrk: [https://github.com/wg/wrk](https://github.com/wg/wrk)

I downloaded using:
wget [https://github.com/wg/wrk/archive/master.zip](https://github.com/wg/wrk/archive/master.zip)

then unzipped:
unzip master.zip

then make:
cd wrk-master
ls:
webs@webs:~/wrk-master$ ls
LICENSE  Makefile  NOTICE  README  [COLOR="Blue"]src[/COLOR]

then after "make":

webs@webs:~/wrk-master$ make
cc -std=c99 -Wall -O2 -c -o obj/wrk.o src/wrk.c
cc -std=c99 -Wall -O2 -c -o obj/aprintf.o src/aprintf.c
cc -std=c99 -Wall -O2 -c -o obj/stats.o src/stats.c
cc -std=c99 -Wall -O2 -c -o obj/units.o src/units.c
cc -std=c99 -Wall -O2 -c -o obj/ae.o src/ae.c
cc -std=c99 -Wall -O2 -c -o obj/zmalloc.o src/zmalloc.c
cc -std=c99 -Wall -O2 -c -o obj/http_parser.o src/http_parser.c
cc -std=c99 -Wall -O2 -c -o obj/tinymt64.o src/tinymt64.c
cc  -o wrk obj/wrk.o obj/aprintf.o obj/stats.o obj/units.o obj/ae.o obj/zmalloc.o obj/http_parser.o obj/tinymt64.o -lpthread -lm

webs@webs:~/wrk-master$ ls
LICENSE  Makefile  NOTICE  [COLOR="Blue"]obj[/COLOR]  README  [COLOR="Blue"]src[/COLOR]  [COLOR="Lime"]wrk[/COLOR]

my understanding is green in the terminal should be an exe, I tried typing wrk, but no go:

webs@webs:~/wrk-master$ wrk
No command 'wrk' found, did you mean:
 Command 'wmk' from package 'wml' (universe)
 Command 'ark' from package 'ark' (universe)
 Command 'wrc' from package 'wine1.4' (universe)
wrk: command not found

What did I miss?

---

### Post by steeldriver on 2013-02-23
since the current directory is not in your executable path (aka $PATH) you need to give the path to the executable file, i.e.

```
**./**wrk
```

---

### Post by xekon on 2013-02-24
Thanks! worked perfect.

---

