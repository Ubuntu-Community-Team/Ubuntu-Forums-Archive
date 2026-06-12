---
title: "Hi all, new to forumn, quick question"
date: 2008-02-12
forum: Packaging and Compiling Programs
---

### Post by fat_boy on 2008-02-12
I am working through Rubianis book on linux drivers and compiliong the hello.c example.

In the book it says it produces a hello.ko file, but when I try to compiile it it produces a hello.o file.   When I try to insmod the hello.o file it fails.

So, the question:   What is the difference between a .ko and a .o file and how can the compiler be told to generate one or the other?

Thanks all in advance for any guidance on this

[modified]

I do get an error  compiling jit.c: ' linux/config.h No such file or directory'.   I wouldnt expect this ti cause a problem with hello.c unless there is a two pass compilation.

I built and am running a tree based on 2.6.22.14 (the same as the Ubuntu Gutsy) OK without problems.

[modified 1]

OK, commenting out all files except hello.c in the makefile does produce a .hello.ko.cmd file that can be loaded with insmod ./hello.ko    so it is a two pass compilation.

Next quesiton then, why dont I see "Hello world" out put to the terminal?


[modified]

OK, the output gors to kern.log

So, the final question,  why is there stuff in the OReilly examples that needs non existant header files?

---

### Post by geraldm on 2008-02-13
You should post enough information so that others can see what the problem is.
It is best to provide the portion of the OReilly examples that are requiring non-existent header files, and a reference to where the full examples can be available.

Gerald

---

