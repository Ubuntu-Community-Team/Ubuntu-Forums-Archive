---
title: "GCC question regarding -l flag"
date: 2008-11-09
forum: Programming Talk
---

### Post by SuperMike on 2008-11-09
Is there a way I can change my .c file such that I do not have to pass -l and -L to include libraries such as pgeasy (for PostgreSQL)? I mean, it would be nice to simply include something at the top of the .c file to make it do the -l stuff, instead.

I'm a newbie with C, by the way. And I've been coming in via the [Large-C implementation of it]("http://ubuntuforums.org/showthread.php?p=2097808") -- where you can make C into a scripting language, which, in the background, compiles things with GCC on the fly and keeps a CRC hash to indicate if the script has changed and whether the program needs recompiling or not.

---

### Post by samjh on 2008-11-10
Well, as far as I'm aware, you can't really do that with gcc.

But you can write a makefile, or even just a shell script, to do the compiling for you so you don't have to do all that extra typing.

Here's a simple makefile:
```
helloworld: hellworld.c
	gcc helloworld.c -o helloworld -I/usr/lib/mylib/include -lmylib
```
Note that the second line begins with a tab character, not just spaces.  Save it as "Makefile" in the same directory as helloworld.c and run "make" in that directory.

Here's more on makefiles: [http://oreilly.com/catalog/make3/book/ch01.pdf](http://oreilly.com/catalog/make3/book/ch01.pdf)

---

### Post by uljanow on 2008-11-10
AFAIK there is no linker that can do that. But as far as shared libraries are concerned you could load them manually (man 3 dlopen).

That C scripting language looks like Pike. :)

---

