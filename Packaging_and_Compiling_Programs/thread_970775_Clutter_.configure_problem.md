---
title: "Clutter ./configure problem"
date: 2008-11-04
forum: Packaging and Compiling Programs
---

### Post by Maya-PSK on 2008-11-04
Hi to all , i'm trying to compile [Clutter]("http://www.clutter-project.org/") on my Intrepid Ibex.
But I've this problem with ./configure:
```

checking for X11... checking for X... no
found
checking for XFIXES extension >= 3... not found
checking for XDAMAGE extension... not found
checking for XCOMPOSITE extension >= 0.4... not found
configure: error: Required backend X11 Libraries not found.

```

What means? How can I solve this problem?

Thanks ;)

EDIT:

Ok , I've just installed cairo-dock-dev , now the ./configure error is :

```
configure: error: Unable to locate required GL headers

```

EDIT:

Ok , ./configure works!
Now make report this error :

```
test-depth.c:14: error: &#8216;raise&#8217; redeclared as different kind of symbol
/usr/include/signal.h:129: error: previous declaration of &#8216;raise&#8217; was here
make[2]: *** [test-depth.o] Error 1
make[2]: Leaving directory `/home/enrico/clutter-0.8.2/tests'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/enrico/clutter-0.8.2'
make: *** [all] Error 2

```

Thanks!

P.S Sorry for my English!

---

