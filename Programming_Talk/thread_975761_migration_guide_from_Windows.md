---
title: "migration guide from Windows?"
date: 2008-11-08
forum: Programming Talk
---

### Post by echohello on 2008-11-08
I have noticed some small differences with C in Windows and C
in linux. Is there a guide for the C programmer of Windows who
wants to migrate to linux?

---

### Post by gnusci on 2008-11-08
I don't know any, unfortunately, but this ebook can be useful

[http://www.advancedlinuxprogramming.com](http://www.advancedlinuxprogramming.com)
[http://www.advancedlinuxprogramming.com/alp-folder](http://www.advancedlinuxprogramming.com/alp-folder)

---

### Post by LaRoza on 2008-11-08
> **echohello said:**
> I have noticed some small differences with C in Windows and C
in linux. Is there a guide for the C programmer of Windows who
wants to migrate to linux?

C is a specification. [Ansi C](http://en.wikipedia.org/wiki/ANSI_C) is the standard and you can safely use that anywhere with a good compiler.

First, figure out if these differences are deviations from the standard. In Windows, you see a lot of "dos.h", "windows.h", "conio.h", etc. These are not standard. 

Second, know the Ansi C library. Second, learn GNU C and POSIX extensions. My wiki should help with that, it has guides for those standards.

Last, if you need what Windows C had, find suitable libraries for Linux. Linux isn't Windows and is more diverse, so you may have more options to sift through. For GUI's, try GTK+, for terminal effects, try ncurses, for graphics and multimedia, try SDL + OpenGL.

gcc is **the** compiler, so learn how to use that as well, in case you haven't started with it. There are many IDE's you can use with it, see the sticky for them, although I use gedit + plugins if I am not using Vim.

---

### Post by gnusci on 2008-11-08
Yeah... you should start reading GCC:

[http://gcc.gnu.org/onlinedoc](http://gcc.gnu.org/onlinedoc)

It is my recommendation too...

---

