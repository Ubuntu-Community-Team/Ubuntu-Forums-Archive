---
title: "[SOLVED] xchat_2.4.3 problem during make"
date: 2005-05-23
forum: Packaging and Compiling Programs
---

### Post by [censored] on 2005-05-23
Can anybody tell me what the problem below means, and/or how to fix it?

/bin/sh ../../libtool --mode=link --tag=CC gcc  -g -O2 -Wall -pipe    -o perl.la -rpath /usr/lib/xchat/plugins -avoid-version -module  perl.lo -Wl,-E -L/usr/local/lib /usr/lib/perl/5.8/auto/DynaLoader/DynaLoader.a -L/usr/lib/perl/5.8/CORE -lperl -ldl -lm -lpthread -lcrypt -ldl -Wl,--export-dynamic -ldl -lglib-2.0

*** Warning: Linking the shared library perl.la against the
*** static library /usr/lib/perl/5.8/auto/DynaLoader/DynaLoader.a is not portable!
gcc -shared  .libs/perl.o  -L/usr/local/lib /usr/lib/perl/5.8/auto/DynaLoader/DynaLoader.a -L/usr/lib/perl/5.8/CORE -lperl -lm -lpthread -lcrypt -ldl /usr/lib/libglib-2.0.so  -Wl,-E -Wl,--export-dynamic -Wl,-soname -Wl,perl.so -o .libs/perl.so
/usr/bin/ld: cannot find -lperl
collect2: ld returned 1 exit status
make[3]: *** [perl.la] Error 1

---

### Post by [censored] on 2005-05-28
Fixed!

> /usr/bin/ld: cannot find -lperl

That's the only bit I needed to understand.

Dan Espen on comp.os.linux.help informed me that that means it was looking for a file caled lperl.so.

$ apt-file search libperl.so
libperl-dev: usr/lib/libperl.so
$ sudo apt-get install libperl-dev

Now compiles fine!

---

### Post by tonybaqain on 2008-09-23
this works great, but if the error still occur then you have to do some steps :

[LIST]
[*]sudo updatedb
[*]sudo locate libperl.so
[*]you'll find something like, depending on the libperl-dev version
```

/usr/lib/libperl.so.5.8
/usr/lib/libperl.so.5.8.8

```
[*]sudo ln -sf /usr/lib/libperl.so.5.8 /usr/lib/libperl.so
[*]sudo ldconfig
[*] have fun :)
[/LIST]

---

