---
title: "Kdevelop3 doesn't work :("
date: 2005-07-24
forum: Programming Talk
---

### Post by dr23 on 2005-07-24
Hi everybody. i post for the first time on this forum.
When i try to build a c++ projet with kdevelop3 (i have installed build essential and kdevelop3) i have these following messages and i don't know why and what to do.

```

cd '/home/nicolas/c' && CC="i586-mingw32msvc-c" CXX="i586-mingw32msvc-c++" LD="i586-mingw32msvc-ld" "/home/nicolas/c/configure" && cd '/home/nicolas/c' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -j1 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... found
checking for working autoconf... found
checking for working automake-1.4... found
checking for working autoheader... found
checking for working makeinfo... missing
checking for C++ compiler default output file name... 
configure: error: C++ compiler cannot create executables
See `config.log' for more details.
*** Sortie avec l'état : 77 ***

```

somebody could help me ?

---

### Post by dr23 on 2005-07-25
i have found my fucking problem. In fact : project option > configure
i write gcc instead of i586-mingw32msvc-c and g++ instead of i586-mingw32msvc-c++
but i don't know what is i586-mingw32msvc-ld ?

---

