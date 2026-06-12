---
title: "Compiled YAPH: Now It Won't Work"
date: 2013-04-01
forum: New to Ubuntu
---

### Post by ctbuzzy on 2013-04-01
I'm trying to install a program called YAPH (Yet Another Proxy Hunter). As far as I can tell, I've successfully configured & installed it by running "./configure," "make," & "sudo make install." I had to work around a problem in the init.c file that was causing errors during "make" & "makel install," but I made the errors go away.

But now that the commands have supposedly succeeded, there's no working program to speak of. It simply isn't there. I can't find it in the dash, & it isn't listed among the recent installations. The "install" command seemed to work in the terminal, but it clearly didn't *install* anything.

Here's what I get on "./config":

loading cache ./config.cache
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... (cached) yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... (cached) gcc
checking whether the C compiler (gcc   ) works... yes
checking whether the C compiler (gcc   ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking how to run the C preprocessor... (cached) gcc -E
checking whether  supports -frepo... (cached) yes
checking for ld used by GCC... (cached) /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... (cached) yes
checking for /usr/bin/ld option to reload object files... (cached) -r
checking for BSD-compatible nm... (cached) /usr/bin/nm -B
checking whether ln -s works... (cached) yes
checking how to recognise dependant libraries... (cached) pass_all
checking for ranlib... (cached) ranlib
checking for strip... (cached) strip
checking for Cygwin environment... (cached) no
checking for mingw32 environment... (cached) no
loading cache ./config.cache within ltconfig
checking whether -lc should be explicitly linked in... (cached) yes
checking for objdir... .libs
checking for gcc option to produce PIC...  -fPIC -DPIC
checking if gcc PIC flag  -fPIC -DPIC works... (cached) yes
checking if gcc static flag -static works... (cached) yes
finding the maximum length of command line arguments... (cached) 73729
checking if gcc supports -c -o file.o... (cached) yes
checking if gcc supports -fno-rtti -fno-exceptions ... no
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking command to parse /usr/bin/nm -B output... ok
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for dlfcn.h... (cached) yes
checking whether a program can dlopen itself... (cached) yes
checking whether a statically linked program can dlopen itself... (cached) no
creating libtool
loading cache ./config.cache
checking for object suffix... (cached) o
checking for executable suffix... (cached) no
checking for ranlib... (cached) ranlib
checking for strip... (cached) strip
checking for extra includes... no
checking for extra libs... no
checking if yaph should be compiled... yes
creating ./config.status
fast creating ./Makefile
fast creating yaph/Makefile
fast creating yaph/docs/Makefile
can't open ./yaph/docs/Makefile.in: No such file or directory
fast creating yaph/docs/en/Makefile
can't open ./yaph/docs/en/Makefile.in: No such file or directory
creating config.h
config.h is unchanged

Here's what I get on "make":

make  all-recursive
make[1]: Entering directory `/home/mklein/Desktop/yaph-0.91'
Making all in yaph
make[2]: Entering directory `/home/mklein/Desktop/yaph-0.91/yaph'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/mklein/Desktop/yaph-0.91/yaph'
make[2]: Entering directory `/home/mklein/Desktop/yaph-0.91'
make[2]: Leaving directory `/home/mklein/Desktop/yaph-0.91'
make[1]: Leaving directory `/home/mklein/Desktop/yaph-0.91'

And here's what I got from "sudo make install":

Making install in yaph
make[1]: Entering directory `/home/mklein/Desktop/yaph-0.91/yaph'
make[2]: Entering directory `/home/mklein/Desktop/yaph-0.91/yaph'
/bin/sh ../admin/mkinstalldirs /usr/local/bin
 /bin/sh ../libtool  --mode=install /usr/bin/install -c -p   yaph /usr/local/bin/yaph
/usr/bin/install -c -p yaph /usr/local/bin/yaph
/bin/sh ../admin/mkinstalldirs /etc/
/usr/bin/install -c -p -m 644 ./yaph.conf /etc/yaph.conf
make[2]: Leaving directory `/home/mklein/Desktop/yaph-0.91/yaph'
make[1]: Leaving directory `/home/mklein/Desktop/yaph-0.91/yaph'
make[1]: Entering directory `/home/mklein/Desktop/yaph-0.91'
make[2]: Entering directory `/home/mklein/Desktop/yaph-0.91'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/mklein/Desktop/yaph-0.91'
make[1]: Leaving directory `/home/mklein/Desktop/yaph-0.91'

Beyond that, there's no information I have that would explain why there's no working program. The closest thing I can find to a working installation is a YAPH .exe file that won't open. Thanks for any help!

---

### Post by tgalati4 on 2013-04-01
Is /usr/local/bin in your path?

```
$PATH
which yaph
man yaph
yaph --verbose
yaph --debug
```

---

### Post by mc4man on 2013-04-02
It's a command line app, 
yaph <engine> [parameters]
read the README in source, ect.

---

