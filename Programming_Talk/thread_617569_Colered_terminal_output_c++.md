---
title: "Colered terminal output c++"
date: 2007-11-19
forum: Programming Talk
---

### Post by monkeyking on 2007-11-19
I'm doing a terminal program in c/c++.

And I wan't to display colored output in terminal.
Does anyone know how to do this?

thanks in advance

---

### Post by nerdzero on 2007-11-19
I think the package you are looking for is called colorgcc.  Can someone verify?

---

### Post by divineleft on 2007-11-19
> **nerdzero said:**
> I think the package you are looking for is called colorgcc.  Can someone verify?

that's for gcc's output. I think he is looking for a colored stdout from the program.

Ncurses would work, otherwise you would need to print out escaped commands (which are terminal specific).

---

### Post by LaRoza on 2007-11-19
Ncurses is exactly what you want, [http://laroza.freehostia.com/LinuxSpecific](http://laroza.freehostia.com/LinuxSpecific)

---

### Post by monkeyking on 2007-11-20
Thanks I'll look into the ncurses stuff.

But the gccolor is also, quite nice.

---

### Post by monkeyking on 2007-11-22
My program should be multiplatform.
And as far as I can tell, ncurses only works on unix.

does anyone know of something similar to ncurses.

---

