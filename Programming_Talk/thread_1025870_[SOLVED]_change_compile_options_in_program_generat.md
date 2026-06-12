---
title: "[SOLVED] change compile options in program generated with automake"
date: 2008-12-30
forum: Programming Talk
---

### Post by monkeyking on 2008-12-30
Hi,
I'me trying to compile and install a program.
This works the old way like 
[PHP]./configure
make
make install
[/PHP]
This works with no problem,
but I want to change som compile options.


Like instead of using gcc I want to use icc,
but also the cflags cxxflags.

But what is the recommend way of changing this.
I can just do a search replace, 
but I have a gut feeling theres a better way of doing this.

theres a hole lot of strange files like
[PHP]
ls config* Make*
config.log     configure     Makeconf.in   Makefile.in     Makefrag.cxx
config.site    configure.ac  Makefile      Makefrag.cc     Makefrag.m
config.status  Makeconf      Makefile.bak  Makefrag.cc_lo
[/PHP]

thanks in advance

edit:
I know I can change all the compile options, wich CC=icc and CXX=icpc,
but If I want to change the install dir,
I can do ./configure prefix=/dir/to/install.

So I guess theres a way to change the defaults,
or atleast get a list.

---

### Post by monkeyking on 2008-12-30
Theres a file called config.site which apparently contains the stuff I was looking for.

also ./configure --help

---

