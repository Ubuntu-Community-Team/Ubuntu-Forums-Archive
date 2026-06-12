---
title: "GCC out of the box on windows"
date: 2007-07-24
forum: Programming Talk
---

### Post by xlinuks on 2007-07-24
Hi
I'm pretty sure it's impossible, but who knows.
Is there an easy way to install GCC on windows through a simple setup.exe installer? (There _is_ one for GTK+)
On Linux I don't have to install it cause it's already there, while on windows I gotta learn anything from scratch to be able to install GCC.

---

### Post by lisati on 2007-07-24
Check out [http://sourceforge.net/projects/gcw/](http://sourceforge.net/projects/gcw/) and [http://gcc.gnu.org/ml/gcc-help/2000-03/msg00120.html](http://gcc.gnu.org/ml/gcc-help/2000-03/msg00120.html)

---

### Post by Mr. C. on 2007-07-24
[http://www.cygwin.com/](http://www.cygwin.com/) provides gcc.  It is trivial to install packages.  Start the setup.exe, select your packages, and go.

MrC

---

### Post by the_unforgiven on 2007-07-24
There are also the [MinGW]("http://www.mingw.org") project and [djgpp]("http://www.delorie.com/djgpp") project that provide windows port of gcc.
MinGW comes in a single setup.exe sort of installer whereas djgpp is shipped as separate zips for every component.

---

### Post by xlinuks on 2007-07-24
Thanks, currently the cygwin setup is downloading the files.

---

