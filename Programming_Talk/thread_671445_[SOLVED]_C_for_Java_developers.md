---
title: "[SOLVED] C for Java developers"
date: 2008-01-18
forum: Programming Talk
---

### Post by xlinuks on 2008-01-18
Hi,
I'm using Java for a few years and I wonder whether there's a tutorial or book for those who start learning C having a (solid) background in Java? I mean the book/tutorial to explain the differences rather than explaining any notion from ground up...

---

### Post by LaRoza on 2008-01-18
> **xlinuks said:**
> Hi,
I mean the book/tutorial to explain the differences rather than explaining any notion from ground up...

The syntax is similiar, other than that, you'll have to learn it from the ground up.

Java has a GC, C doesn't. Java doesn't have pointers, whereas pointers are an integral part of C.

You'll fly through the sections on variables (except pointers), decisions, and control statements.

See my wiki for C tutorials.

For the best reference, get K&R.

---

### Post by Wybiral on 2008-01-18
Forget everything you know when trying to jump between Java and C code. Small snippets may LOOK similar (the same goes for C and C++ as well), but they are completely different. IMO you will be better off just learning C as though you never knew Java. You can still use some of your design patterns (and, in fact, you can even use a form of pseudo OOP in C) but you're going to have to learn a lot more about the machine like managing memory allocation, juggling pointers, not having pretty namespace packages, and living without enforced public/private declarations. Oh yeah, and no function overloading either :)

---

### Post by xlinuks on 2008-01-19
Well, thanks both for these advices, I forgot to mention that I have an assembly background (on Linux and windows), thus I know (very well) the difference between Java and C. I'm familiar with things like stack, CPU registers (32 & 64), the difference between "test" and "cmp", syscalls, thus programming in C wouldn't be difficult for me, I started reading a few books (about C), and along the lines there's lots of things I already know and a few I don't yet, so I actually spend a lotta time reading known things, thus I was wondering if there's some book for developers like me. Btw if someone's interested why C (not C++ or alike) - because it's the lingua franca in Linux, and since I moved to linux a long ago I practically can't help improving it ( the apps I think should be improved).
I'm working over a file manager, it works fast (faster than Krusader and Thunar, especially when dealing with directories with thousands of files), however I have one issue, the Java startup time makes it seem not so fast and lightweight.
([http://xlinuks.googlepages.com/fjfm0.6.03.jpg](http://xlinuks.googlepages.com/fjfm0.6.03.jpg))
All my friends say that, so I guess if I'm gonna share it with the community (to be an alternative to Nautilus) I'll have to rewrite it in C.. It's just because the File Manager in Ubuntu is one of the top 3 painful issues on my blacklist.

---

### Post by amo-ej1 on 2008-01-19
Well java and c are completely different. Since C is lacking every single concept of object orientation (somehow they can be simulated, but still it isn't a language feature, only a derivative). So you'll basicly need another mindset.
It's the same when you're looking a a functional programming lanuage (scheme, lisp, haskell) for the first time as well, then you also enter this 'everything you know is wrong' phase.
Your assembly background might cone in handy so you won't encounter that much pointer issues i assume, but again, assembly lacks any form of structure where c has structure, so again a different mindset.

nevertheless don't let this bother you and simply write some code, you'll get the hang of it soon enough. And don't forget to apt-get install manpages-dev which is a c level replacement for the api docs

---

### Post by xlinuks on 2008-01-19
Ok, thanks, I installed manpages-dev, how do I use it?

---

### Post by Balazs_noob on 2008-01-19
just type into the terminal the function name you
want to know more about..
like
> 
man printf
man shmget


also this can be helpful
[http://www.gnu.org/software/libc/manual/](http://www.gnu.org/software/libc/manual/)

---

### Post by wolfbone on 2008-01-19
> **xlinuks said:**
> Ok, thanks, I installed manpages-dev, how do I use it?

$ man man

The manpages-dev package contains man pages from the System Calls [2] and C Library Functions [3] sections. If you already know the GNU C library and *nix C programming and know what you are looking for, the man pages are fine. 

However, if you want to learn what is in the GNU C library and how best to use it, you'll be better off installing the 'info' pages manual (in the glibc-doc package) and reading through (some of) it.

Developing with C involves rather more than just the language itself of course and you'll probably also want to read about gdb, make, automake, libtool etc. at some point. 

[http://www.informit.com/content/downloads/perens/0130091154.pdf](http://www.informit.com/content/downloads/perens/0130091154.pdf)
[http://sourceware.org/autobook/autobook/autobook_toc.html](http://sourceware.org/autobook/autobook/autobook_toc.html)

Then there are the libraries you're probably going to want to use such as GLib and GTK+...

---

### Post by LaRoza on 2008-01-19
> **xlinuks said:**
> Well, thanks both for these advices, I forgot to mention that I have an assembly background (on Linux and windows), thus I know (very well) the difference between Java and C. I'm familiar with things like stack, CPU registers (32 & 64), the difference between "test" and "cmp", syscalls, thus programming in C wouldn't be difficult for me, I started reading a few books (about C), and along the lines there's lots of things I already know and a few I don't yet, so I actually spend a lotta time reading known things, thus I was wondering if there's some book for developers like me. Btw if someone's interested why C (not C++ or alike) - because it's the lingua franca in Linux, and since I moved to linux a long ago I practically can't help improving it ( the apps I think should be improved).
I'm working over a file manager, it works fast (faster than Krusader and Thunar, especially when dealing with directories with thousands of files), however I have one issue, the Java startup time makes it seem not so fast and lightweight.
([http://xlinuks.googlepages.com/fjfm0.6.03.jpg](http://xlinuks.googlepages.com/fjfm0.6.03.jpg))
All my friends say that, so I guess if I'm gonna share it with the community (to be an alternative to Nautilus) I'll have to rewrite it in C.. It's just because the File Manager in Ubuntu is one of the top 3 painful issues on my blacklist.

With that background, you will find C to be high level assembly with a familiar syntax.

I'll try the file manager. (I am a Thunar fan myself...)

Have you tried midnight commander? Some prefer it.

---

### Post by pmasiar on 2008-01-19
Midnight commander is in C, mature and stable, but still under development (even if I cannot say "active" - but far from dead), and reading it you can see some code written by [http://en.wikipedia.org/wiki/Miguel_de_icaza](http://en.wikipedia.org/wiki/Miguel_de_icaza) who was it's original developer.

---

