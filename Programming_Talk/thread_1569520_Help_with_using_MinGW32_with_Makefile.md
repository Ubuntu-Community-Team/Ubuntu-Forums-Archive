---
title: "Help with using MinGW32 with Makefile"
date: 2010-09-06
forum: Programming Talk
---

### Post by sevenn30000 on 2010-09-06
How do I use MinGW32 on linux with a makefile to build a program for windows ?

Thank you !

---

### Post by foxmuldr on 2010-09-07
> **sevenn30000 said:**
> How do I use MinGW32 on linux with a makefile to build a program for windows ?

Thank you !

I do not know how to do this. But I know a project that uses MiniGW32 to handle some of its operations. Download CodeLite ([www.codelite.org](www.codelite.org), or search for CodeLite on SourceForge), and it will install the CodeLite + wxWidgets + MiniGW32 bundle, and you can see how it uses those commands at various places.

Best of luck!

---

### Post by and.dmitry on 2010-09-07
You have to install mingw32 cross-compiler toolchain:
```
sudo apt-get install mingw32 mingw32-binutils mingw32-runtime
```
Then you can use i586-mingw32msvc-gcc (and other i586-mingw32msvc-* tools) to build programs pretty much the same way it's done with native gcc.
Note that:
[LIST]
[*]mingw32 has it's own include and lib dirs in /usr/i586-mingw32msvc/.
[*]If your program depends on some libraries, they must be build with mingw32 too.
[/LIST]
Here's a small example [http://wiki.wxwidgets.org/Cross-Compiling_Under_Linux#Example_usage]("http://wiki.wxwidgets.org/Cross-Compiling_Under_Linux#Example_usage")

Hope this helps.

---

