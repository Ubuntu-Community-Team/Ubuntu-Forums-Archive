---
title: "graphics in gcc"
date: 2010-03-05
forum: Programming Talk
---

### Post by noobad@linux on 2010-03-05
hi .......gcc doesnt have garphics.h in ubuntu10.9 whats its replacement ???

---

### Post by Zugzwang on 2010-03-05
The answer is simple: [http://www.lmgtfy.com/?q=graphics.h+Ubuntu](http://www.lmgtfy.com/?q=graphics.h+Ubuntu)

---

### Post by nebu on 2010-03-05
gcc is a c compiler..... if u want to use graphics with gcc.... u need to use a library which provides these graphics facilities and then just tell gcc that u are using these graphics libraries and ask gcc to link the required libraries to your executable.... and voila.... u have graphics using gcc....

u might like to try the following libraries -
1. glut, glu etc
2. sdl

if u want to design user interfaces like most other programs in ubuntu, u can also try....
1. gtk
2. qt
3. tk

---

### Post by noobad@linux on 2010-03-07
thanx...

---

