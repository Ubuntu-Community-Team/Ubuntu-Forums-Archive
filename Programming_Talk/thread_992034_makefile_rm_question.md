---
title: "makefile/ rm question"
date: 2008-11-24
forum: Programming Talk
---

### Post by bovus on 2008-11-24
I trying to write a makefile for a programming assignment.  In my main directory I have the makefile and a folders called src.  In the src directory I have two other directories with source code in both of them.  I want to be able to run the one makefile in the main directory and have it remove all temp files (*~, *.o, \#*, ...) in all of the sub-directories of the main directory while keeping the sub-directories in-tact. Is there a way to do this with the 'rm' command or a makefile trick?

---

### Post by nvteighen on 2008-11-24
Use the rm command. A Makefile is just a script that executes shell commands according to dependencies.

There's a variant I don't understand well what advantages it brings, which consists in appending @ to shell commands (and not when calling programs, like the compiler). So, according to that, you'd write @rm (and @echo, etc.), but it's the same.

---

