---
title: "Graphics programming in Ubuntu 9.10 using C++!!!!!!"
date: 2010-10-18
forum: Programming Talk
---

### Post by ankurtiwari044 on 2010-10-18
how to use C or C++ for graphics programming in ubuntu 9.10?? 
can we use GCC for the same!!!
or any other c/c++ compiler for that.....


HELP PLEASE!!!!!

ANKURTIWARI044

---

### Post by James78 on 2010-10-18
Of course you can. Gcc and G++ are excellent compilers, and I use them myself. But any compilers should work as long as you have good code. :)

---

### Post by programmer123 on 2010-10-18
You need gtk
_[http://www.gtk.org/](http://www.gtk.org/)_

---

### Post by koushik_fly on 2010-10-18
> **James78 said:**
> Of course you can. Gcc and G++ are excellent compilers, and I use them myself. But any compilers should work as long as you have good code. :)


Thank u.....found it very useful

---

### Post by nvteighen on 2010-10-18
You use a library... there are GUI tookits (Qt, GTK+), there are full-fledged 3D libraries (OpenGL), there's even the possibility of hacking the graphical server itself (Xlib)... No traditional language will give you access to graphics by default, not even in Windows (AFAIK, the thing is that Visual C++ will automatically link your program to the needed libraries)

---

### Post by shawnhcorey on 2010-10-18
I recommend you use Glade to create you GUI.  Open Application -> Ubuntu Software Centre and type "glade" in the search box.  Install the Glade Interface Designer.

See [http://glade.gnome.org/](http://glade.gnome.org/)

---

### Post by fct on 2010-10-19
And if by "graphics" you don't mean "GUI" this is a nice choice:

[http://www.libsdl.org/](http://www.libsdl.org/)

---

