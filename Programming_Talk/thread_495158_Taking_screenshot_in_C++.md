---
title: "Taking screenshot in C++"
date: 2007-07-07
forum: Programming Talk
---

### Post by edtechre on 2007-07-07
Howdy,

Does anyone know how to write a C++ program that will take a screemshot in Linux (or know where to find one)?

---

### Post by duff on 2007-07-08
If you're not looking for anything fancy, install imagemagick and use ```
system("import -window root screen.png")
``` will do the trick.

---

### Post by hod139 on 2007-07-08
If you go the imagemagick route, there is a C++ api available so you do not have to use a system dependent system call.  [http://www.imagemagick.org/Magick++/](http://www.imagemagick.org/Magick++/)

---

