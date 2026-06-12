---
title: "Compiling Boost library for mingw32 on linux..."
date: 2007-08-14
forum: Packaging and Compiling Programs
---

### Post by rksk16it on 2007-08-14
Hi friends :)
I want to install Boost library for mingw32 compiler installed on my Ubuntu. I already have native libraried for boost...but i need to cross-compile programs for windows.

I tried to compile Boost with mingw32 compiler, the compilation was successful, but....it produced "*.so" files, but i need "*.a" files, so that they can be used with mingw.

I read other places about cross-compiling, when creating this thread...but all those are specific to wxWidgets, whose "./configure" has an option like "--host=i586-mingw", but this is not so with Boost.

If anyone know any way to achieve that, or know any links which can help me, it will be nice :)

And if anyone is sure this cant be done, pls tell me that too....

Thanks :)

---

### Post by Alex.Gorban on 2008-08-14
I'm trying to do the same. Is there any progress in solving the problem?

---

### Post by CodeAlias on 2009-01-06
Hi,

You can try to add AC_DISABLE_SHARED to the configure.ac file then run autoconf again.

See [Using mingw and libtool to cross-compile static libraries]("http://www.codealias.info/technotes/using_mingw_and_libtool_to_cross_compile_static_libraries") for an example.

Hope it helps.
---
[Networking and Coding Articles]("http://www.codealias.info/")
[Subscribe]("http://feedproxy.google.com/codealias")

---

