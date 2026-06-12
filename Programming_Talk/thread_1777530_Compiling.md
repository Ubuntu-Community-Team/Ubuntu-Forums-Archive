---
title: "Compiling ?"
date: 2011-06-07
forum: Programming Talk
---

### Post by rpmp on 2011-06-07
how to compile a program in ubuntu for it to work on windows.

---

### Post by lisati on 2011-06-07
*Thread moved to **Programming Talk**.*

---

### Post by rng on 2011-06-07
I don't think you can make an exe file in ubuntu/linux. If you want to make one program and have it run both on linux and windows, make java program.

---

### Post by cgroza on 2011-06-07
Check cross compiling.

---

### Post by rpmp on 2011-06-07
> **rng said:**
> I don't think you can make an exe file in ubuntu/linux. If you want to make one program and have it run both on linux and windows, make java program.

im making it with ubuntu but i want it to run on windows.

---

### Post by Ghostmn on 2011-06-07
> **rpmp said:**
> im making it with ubuntu but i want it to run on windows.

What language are you using? EDIT Sorry for my miss-understanding. But do you mean Compiling a package like say gimp on ubuntu and running what you compiled on windows?

---

### Post by rng on 2011-06-07
This link may be useful for you: 

[http://en.wikipedia.org/wiki/Cross_compiler](http://en.wikipedia.org/wiki/Cross_compiler)

---

### Post by JupiterV2 on 2011-06-08
Creating a '.exe' on Linux IS possible. You need to either a) create a cross-compiler yourself, or, b) use mingw to cross-compile. In my personal experience, however, I found it easier to install msys (a minimal POSIX terminal/environment for windows which, coincidentally, also uses mingw as its compiler) so can more reliably test your program directly on the same computer. If you don't have access to a windows computer, then you will have to do what has already been suggested and test using WINE.

This, of course, assumes you're compiling a language like C or C++.

---

### Post by simeon87 on 2011-06-08
It can be done, as others have suggested, but you've given us too little information to be very specific. It depends on the programming styles, the libraries, the compiler, etc.

---

