---
title: "fmod error in gcc"
date: 2008-05-02
forum: Packaging and Compiling Programs
---

### Post by seleciii44 on 2008-05-02
hi. I have a very big number which is bigger than the bounds of long int.Thus i use double. The problem is i have to use it's mod value and the '%' operator doesn't works with the double type. There is a function "fmod" in math.h library but although it seems a ansi c function, gcc gives compiling error :  "undefined reference to `fmod'" . It's too late to change my design. waiting for your help...
 thankss..

---

### Post by notincamics on 2009-06-09
when compiling the program must be use '-lm'.

example: gcc -lm example.c -o example

---

