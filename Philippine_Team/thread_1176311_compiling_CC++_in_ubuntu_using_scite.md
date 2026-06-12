---
title: "compiling C/C++ in ubuntu using scite"
date: 2009-06-02
forum: Philippine Team
---

### Post by Lila_IT_CMU on 2009-06-02
hello!...


pano po ba mag compile ng C/C++ code sa Ubuntu???
please help

---

### Post by loell on 2009-06-02
I don't think you can, it's an editor, not a full blown IDE,
you most likely need to invoke **make** if there is a makefile, or gcc itself if it must.

---

### Post by Lila_IT_CMU on 2009-06-02
ah ok.. how to make a makefile? or the terminal commands to compile???
pls help

---

### Post by jsgotangco on 2009-06-02
[http://www.network-theory.co.uk/docs/gccintro/gccintro_16.html](http://www.network-theory.co.uk/docs/gccintro/gccintro_16.html)

---

### Post by pogztimz on 2009-06-03
> **Lila_IT_CMU said:**
> ah ok.. how to make a makefile? or the terminal commands to compile???
pls help

```
gcc filename.c
``` u should be in the current folder where filename.c is located.


i highly recommend "Anjuta" it is available in the repositories.
happy coding tol.. :D

---

### Post by frustphil on 2009-06-03
> **Lila_IT_CMU said:**
> hello!...


pano po ba mag compile ng C/C++ code sa Ubuntu???
please help

for GUI-less C:
> gcc filename.c -o file

---

### Post by kiminaiseah on 2009-06-03
> **Lila_IT_CMU said:**
> hello!...


pano po ba mag compile ng C/C++ code sa Ubuntu???
please help

you have first this ff. rep

apt-get get module-assistant mawk gawk bison flex make automake autoconf module-assistant -y

after that.

m-a prepare

yes

yes

then thats it you may now use make inside the folder have c codes

---

### Post by jsgotangco on 2009-06-03
btw, don't forget to install the build-essential package first :P

---

