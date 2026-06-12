---
title: "C/C++ programing for Linux"
date: 2006-11-05
forum: Programming Talk
---

### Post by Phantom784 on 2006-11-05
Does anyone have any resources/tutorials/advice on c/c++ programing in linux?  I pretty much know the basics of the two languages (altough I haven't used them for a while), but I'd like to learn how to use them in a linux environment, including ./configure and make files, static and dynamic libraries,  and stuff like that.  Also, when should you use c over c++ and visa versa?

Thanks in advance for any help!

---

### Post by .t. on 2006-11-05
me too!

---

### Post by TheWizzard on 2006-11-06
KDevelop 3 is a nice programming environment for kde.
it has template for using make.

---

### Post by GeneralZod on 2006-11-06
> **TheWizzard said:**
> KDevelop 3 is a nice programming environment for kde.
it has template for using make.

I really didn't like kdevelop the first time I tried it, but I've just started my first Linux/ KDE app and it's actually pretty cool - it generates all the configure scripts and makefiles for you, which is good, as I've never looked into how to do it myself ;)

I think there's a mode for straight C/C++ if you don't want to write a KDE app.

---

### Post by chaosgeisterchen on 2006-11-06
I can second the fact that KDevelop does the job very well.

---

### Post by TheWizzard on 2006-11-07
> **GeneralZod said:**
> 
I think there's a mode for straight C/C++ if you don't want to write a KDE app.

indeed. i use C for calculating stuff. 
the simplest is to use the "hello world" template.

---

### Post by loell on 2006-11-07
;)  this should have been in the programming section

anyway, i beleive [This tutorial]("http://bo.majewski.name/bluear/gnu/GTK/plain/index.htm") covers the basics

---

### Post by TheWizzard on 2006-11-07
> **loell said:**
> ;)  this should have been in the programming section

anyway, i beleive [This tutorial]("http://bo.majewski.name/bluear/gnu/GTK/plain/index.htm") covers the basics

not what i meant. this link explains a gtk project. with hello world as an example. 

the hello world template creates a minimal piece of source code (see below) + a bunch of additional files. 
there's also a template for make-based programs. just play around :-D 

```

#ifdef HAVE_CONFIG_H
#include <config.h>
#endif

#include <stdio.h>
#include <stdlib.h>

int main(int argc, char *argv[])
{
  printf("Hello, world!\n");

  return EXIT_SUCCESS;
}

```

---

### Post by loell on 2006-11-07
yup , i know ;) 

you were talking about kdevelop, so i guess, its the hello world template that comes with it.

the above link is for c gtk hello world, with the basic of using autotools.

---

### Post by matthew on 2006-11-07
I've moved this to an area where it is more likely to get noticed by people with lots of experience.

---

### Post by Phantom784 on 2006-11-07
thanks for moving it, i didn't notice the programming forum.  also, thanks for all the advice.

---

### Post by Phantom784 on 2006-11-07
Are there any good tutorials for doing simple console programs with kdevelop.  Everything I could find is for KDE applications.  Also, when I try to build the included hello world program, I get

```
cd '/home/user/programs/hello_world' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -f Makefile.cvs && cd '/home/user/programs/hello_world/debug' && CFLAGS="-O0 -g3 " "/home/user/programs/hello_world/configure" --enable-debug=full && cd '/home/user/programs/hello_world/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -k 
aclocal
aclocal: configure.in: 8: macro `AM_PROG_LIBTOOL' not found in library
make: *** [all] Error 1
*** Exited with status: 2 ***
```

---

### Post by loell on 2006-11-07
install automake and autoconf
and libtool

---

### Post by Phantom784 on 2006-11-07
Installing libtool did the trick for hello_world in kdevelop.  However, I also tried the GTK Hello World you (loell) gave earlier and everything works up untill I run ./configure, where it gives me two errors

```
./configure: line 2976: syntax error near unexpected token `DEPS,'
./configure: line 2976: `PKG_CHECK_MODULES(DEPS, gtk+-2.0 >= 2.2 glib-2.0 >= 2.2)'
```
I can only assume the config file wasn't generated correctly.  However, I didn't get any errors from the autotools.

---

### Post by loell on 2006-11-07
my apologies,

 that tutorial is very outdated , but the basic principle is still there,
 if you are really interested in learning autotools
 
 then you should download and read the autotools tutorial pdf
 [http://www-src.lip6.fr/homepages/Alexandre.Duret-Lutz/dl/autotools.pdf]("http://www-src.lip6.fr/homepages/Alexandre.Duret-Lutz/dl/autotools.pdf")

 it also has a "hello world" tutorial section.

---

### Post by Absurd on 2006-11-07
I used [this](http://www.openismus.com/documents/linux/automake/automake.shtml) tutorial to liberate myself from the use of IDE's. I now just use gedit for editing C/C++ code.

---

### Post by lakshmanan on 2011-09-18
how should i do program in linux environment

---

### Post by N1GHTS on 2011-09-18
> **lakshmanan said:**
> how should i do program in linux environment

Kinda strange, resurrecting a 5 year old post only to ask the very same question the original poster asked, having probably not read the responses of the thread or search the forum for other answered threads of this very same topic, or even use Google for more information on one of the most highly documented subjects on the internet. 

And yet, being your first post, it means you went out of your way to register and write to this post, perhaps more effort than simply reading the answers already posted on this thread.

I only took the time and effort of responding to your comment because you are a fascinating enigma, a human embodiment of a software bug, a cup both half empty and half full, just simply fascinating.

But to answer your question, perhaps in turn rubbing your magical fairy dust onto me for good luck, [read this tutorial]("http://www.network-theory.co.uk/docs/gccintro/gccintro_54.html") and do it, for as simple as it seems to be, you can't expect to crawl without arms and legs.

---

