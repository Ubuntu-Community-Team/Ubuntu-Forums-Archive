---
title: "How to compile gtk with Code::blocks"
date: 2007-07-11
forum: Programming Talk
---

### Post by Canis familiaris on 2007-07-11
Hi there
I use Code::blocks for compiling terminal programs. Lately I want to compile gtk programs using Code::blocks. However when I try to compile a gtk app. It is not able to find the gtk/gtk.h header files and libraries. And receive errors.
```
ERROR: gtk/gtk.h: No such file or directory
```
I have already installed th libgtk2.0-dev package and have successfully compiled it in terminal.
Is there any way so that I can compile GTK programs in Codeblocks?

---

### Post by kknd on 2007-07-11
You  need to include the libraries. (/usr/include/gtk-2.0) and etc, in the build / project options.

---

### Post by Canis familiaris on 2007-07-11
Well I set up options globally since I wanted to use code::blocks just to practice gtk.
I went to Settings->Compilers and Debuggers and added:
To the other options in compiler:
```
`pkg-config --cflags gtk+-2.0 `
```
And to the other option in linker:
```
`pkg-config --libs gtk+-2.0 `
```
Anyway thanks.

---

