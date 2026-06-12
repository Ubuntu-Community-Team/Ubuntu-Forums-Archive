---
title: "Cross Compiling for Windows"
date: 2010-10-09
forum: Packaging and Compiling Programs
---

### Post by roadkillguy on 2010-10-09
I have a nice program utilizing OpenGL and SDL.  It's running flawlessly, I just need to bring it to windows.

I've never had to cross compile before, where do I start?  Utilizing my current makefile would be a plus.

Thanks!

---

### Post by and.dmitry on 2010-10-10
install mingw toolchain
```
sudo apt-get install gcc-mingw32 mingw32-binutils mingw32-runtime
```
You'll find compilers, other tools, headers and libs in /usr/i586-mingw32msvc/ .
Note that you'll also have to build all the libs you program depends on with this toolchain.

---

### Post by roadkillguy on 2010-10-10
How exactly do I implement that into a makefile?

---

