---
title: "KDevelop SDL/OpenGl"
date: 2006-07-01
forum: Programming Talk
---

### Post by tehDeuce on 2006-07-01
How do you compile a SDL project that uses OpenGl in KDevelop?  I wrote a program in emacs which I could compile with the command "gcc -Wall -ansi program.c -o program -lGL -lGLU -lm `sdl-config --cflags --libs`", but I can't figure out how to get it to compile in KDevelop.

---

### Post by vasdee on 2006-07-01
[QUOTE=tehDeuce]How do you compile a SDL project that uses OpenGl in KDevelop?  I wrote a program in emacs which I could compile with the command "gcc -Wall -ansi program.c -o program -lGL -lGLU -lm `sdl-config --cflags --libs`", but I can't figure out how to get it to compile in KDevelop.[/QUOTE]

What a kwinky-dink! It just so happened i had the same issue last week :)
On the right hand side of kdevelop there should be a tab for "automake manager". Expand it and then click the little tool button in the bottom window pane...In the 2nd notebook tab of the popup (libraries), you should have the following linked....
```
-lGLU
-lGL
$(LIBSDL_LIBS )
```

then just run configure and build the project. :)

---

### Post by tehDeuce on 2006-07-02
Thanks.  That worked perfectly.

---

### Post by Grellin on 2007-09-10
I must be really screwing this thing up. I added the -lGL and -lGLU like you said and redid the configure and this is what I get:

cd '/home/grellin/sadfdd/debug/./src' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -k sadfdd
Makefile:467: *** missing separator. Stop.
*** Exited with status: 2 ***

Pretty new to Linux so any help is appreciated.

---

### Post by Grellin on 2007-09-12
Never mind. I added those libraries in CodeBlocks and it worked like a charm. Thanks. :guitar:

---

