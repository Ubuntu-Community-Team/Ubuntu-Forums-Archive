---
title: "GCC tutorials"
date: 2006-10-10
forum: Programming Talk
---

### Post by mavix on 2006-10-10
Where can I find good GCC tutorials? I could find nothing usefull in Google.

---

### Post by public_void on 2006-10-10
You could try looking at the [GCC manuals](http://gcc.gnu.org/onlinedocs/). However there complicated but do cover everything about GCC.

---

### Post by amo-ej1 on 2006-10-10
What exactly do you want to do ? Learn programming in C  ? Or something else ?

---

### Post by mavix on 2006-10-10
I am still learning to program in C, but I am using Visual C++ 6.0 in Windows, and not all of the commands are the same, I think.

---

### Post by loell on 2006-10-10
autotools is the way, these are command line tools for managing and builing c source projects.

but for most basic part, if your just programming through standard library
ie (stdio.h)

i think

gcc -o filename.c name_of_program.o

will do :)

---

### Post by amo-ej1 on 2006-10-11
The c/c++ language specification will not change, the API you are using will chance (given that you are programming win32 or MFC). So given that you're just starting there's only a small chance you're already doing graphical or window specific things. So each piece of code you've written this far should in fact compile perfectly with gcc/g++.

---

### Post by mavix on 2006-10-11
> **loell said:**
> autotools is the way, these are command line tools for managing and builing c source projects.

but for most basic part, if your just programming through standard library
ie (stdio.h)

i think

gcc -o filename.c name_of_program.o

will do :)
Thanks

---

### Post by MWAAAHAAA on 2006-10-11
> **loell said:**
> autotools is the way, these are command line tools for managing and builing c source projects.


I tend to disagree. Autotools are much too complicated IMHO and unless you are writing programs for a very wide range of platforms, I would recommend anyone to stick with simple, yet well-written, Makefiles.

---

