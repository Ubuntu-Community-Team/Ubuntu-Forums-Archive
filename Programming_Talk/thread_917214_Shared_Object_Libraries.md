---
title: "Shared Object Libraries"
date: 2008-09-11
forum: Programming Talk
---

### Post by HexJunkie on 2008-09-11
On Windows, if you compile a DLL with certain libraries added to the linker settings, then a program that uses the new DLL does not need to link to the other libraries as well.

For example, lets say I compile "MyLib" and link it with SDL and OpenGL.

If I compile "MyProgram", all I have to link with is "MyLib", not SDL and OpenGL.

Do shared objects on Linux work this way as well?

Thanks!

---

### Post by snova on 2008-09-11
Yes. However, certain build tools might link them anyway (it won't hurt, of course) as a relic from when only static libraries were possible. I think pkg-config is to blame.

---

### Post by rnodal on 2008-09-11
Just like in windows, you also need those library installed. As long as you, for example, don't make a call to a function from those extra libraries (SDL, OpenGL) you will be find. 

> pkg-config is a helper tool used when compiling applications and libraries. It helps you insert the correct compiler options on the command line so an application can use  gcc -o test test.c `pkg-config --libs --cflags glib-2.0`  for instance, rather than hard-coding values on where to find glib (or other libraries). It is language-agnostic, so it can be used for defining the location of documentation tools, for instance.

I don't think pkg-config has anything to do with it. :)

-r

---

