---
title: "A libtool question"
date: 2010-04-07
forum: Programming Talk
---

### Post by y50a7XpWRH66IV on 2010-04-07
Hi everyone,

I have a program which is written with this file structure:
```

   /src
      main.c
      one.c
      two.c
      /plugins
          /libmylib
              libmylib.c

```

I would like to compile libmylib.c as a .so file and place it underplugins.

Currently, my make file under /libmylib is as follows:
```
libmylibdir= /
libmylib_LTLIBRARIES=libmylib.la
libmylib_la_SOURCES=libmylib.c
libmylib_la_LDFLAGS= -lc -lgcc -avoid-version

```

When I build the program in eclipse, libmylib.so is generated under /src/modules/libmylib/.libs

What changes should I make so that libmylib.so is built in /src/modules?

Thank you :)

---

