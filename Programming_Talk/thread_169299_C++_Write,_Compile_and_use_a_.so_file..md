---
title: "C++: Write, Compile and use a .so file."
date: 2006-05-02
forum: Programming Talk
---

### Post by Kimm on 2006-05-02
Well, I think the thread title is pretty self descriptive.

I'm working on a project that I would like to divide into several parts, one base library and interfaces.
My Current way of doing this is to compile the base and interface as object files, and then link them, this works, but if you want to install several interfaces, dividing it into several pieces would be more logical.

My Program will incude one base library (the .so), one ncurses interface and one GTK interface. Possibly a simple non-ncurses interface, and if the project becomes popular, maby I'll learn Qt, or perhaps someone else can write a Qt interface.

My project is as of now, top secret and it will be revealed on these forums, and posted on SourceForge when it is completed.

(Ps.

Does anyone know if website hosting on SourceForge is free of charge?)

---

### Post by Kimm on 2006-05-03
/bump

---

### Post by maulattu on 2006-05-04
if you wanna use dynamic libraries you should take a look at
[www.advancedlinuxprogramming.com](www.advancedlinuxprogramming.com)
you can download the book (and the examples too). in the first chapter there's a good explaination about dynamic libraries (how to create them, how to use them)

---

### Post by lnostdal on 2006-05-04
i originally learnt the .so-thing from this: [http://users.actcom.co.il/~choo/lupg/tutorials/libraries/unix-c-libraries.html](http://users.actcom.co.il/~choo/lupg/tutorials/libraries/unix-c-libraries.html)

also see:
[http://gcc.gnu.org/onlinedocs/gcc/index.html#toc_Invoking-GCC](http://gcc.gnu.org/onlinedocs/gcc/index.html#toc_Invoking-GCC)

oh, and you should take a look at Scons (way better than make)

---

### Post by curtis on 2006-05-04
About your question about Sourceforge, yes I believe it is free.

---

### Post by Kimm on 2006-05-06
Thanks, this realy helps out!

---

