---
title: "KDevelop &amp; aclocal errors"
date: 2006-11-02
forum: Programming Talk
---

### Post by CurtyD13 on 2006-11-02
I've recently upgraded to edgy and since then I can't get a new project in KDevelop to compile. I start a new simple "Hello World" project and then I "Run automake & friends", but all I get is this:
```

cd '/home/curty/Documents/Programming/core' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -f Makefile.cvs
aclocal
make: aclocal: Command not found
make: *** [all] Error 127
*** Exited with status: 2 ***

```

I do have build-essential and libtool installed. Any help would be greatly appreciated.

---

### Post by CurtyD13 on 2006-11-02
OK so all I had to do was install automake which I thought I already had installed.

---

### Post by Jbloudg20 on 2007-01-24
Thanks for posting your solution! It helped me out.

---

### Post by tessmonsta on 2008-02-23
Me too! Thanks!

---

