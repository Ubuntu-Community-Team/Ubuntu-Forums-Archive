---
title: "erasing printed characters from terminal"
date: 2009-05-13
forum: Programming Talk
---

### Post by pipenor on 2009-05-13
Hello,
I am writing a program in which i want to emulate the capability of the terminal to erase characters after they are printed.
For example:
When i press the up arrow in the terminal the last command i typed is printed and when i press backspace i can erase some characters from it. However when a programs printf/write some data to stdout they can't be simply erased with backspace.
Is there any functions in order to achieve this functionality?

Thanks in advance.

---

### Post by dwhitney67 on 2009-05-13
Look into the ncurses library.  It will have the functions for doing exactly what you need.

---

