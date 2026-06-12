---
title: "Compile a window .exe from a cross-platform program, on Linux?"
date: 2009-03-04
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2009-03-04
I know this is possible and it's been done before. But I just can't find anything with forum search.

So how can I compile an application for windows, on my Ubuntu? And the program needs SDL, SDL_image, SDL_mixer, and SDL_ttf.

Thanks.

---

### Post by agim on 2009-03-04
try wine
[http://www.winehq.org/](http://www.winehq.org/)

---

### Post by simeon87 on 2009-03-04
> **agim said:**
> try wine
[http://www.winehq.org/](http://www.winehq.org/)

Wine is for running, not for compiling...

---

### Post by Simian Man on 2009-03-04
You likely won't find a satisfactory way to do this.  Especially using libraries.  Just find a Windows machine with a compiler.

---

### Post by Tibuda on 2009-03-04
You can install MingW32 compilers from the repositories.

---

### Post by crazyfuturamanoob on 2009-03-04
How can I use mingw?

I don't have a windows, and I don't know anything about compiling stuff on windows. (like linking sdl)

---

### Post by cmat on 2009-03-04
Either get a program like Dev-C++ (comes with a Borland compiler I think) and run it under Windows. I think you can cross compile with Mingw but I never used it.

---

### Post by Tibuda on 2009-03-04
> **crazyfuturamanoob said:**
> How can I use mingw?
I don't have a windows, and I don't know anything about compiling stuff on windows. (like linking sdl)
It's the same as gcc.

You won't be able to link your native Linux SDL. You need to download the windows SDL source code and compile the library using MingW32. I can't help very much, but [this tutorial]("http://wiki.wxwidgets.org/Cross-Compiling_Under_Linux") teachs how to do it with wxWidgets. Once you have your compiled windows library, you can link your program using mingw compiler, as you would do with gcc.

EDIT: I believe this link is what you are looking for: [http://www.libsdl.org/extras/win32/cross/README.txt](http://www.libsdl.org/extras/win32/cross/README.txt)

---

### Post by crazyfuturamanoob on 2009-03-04
> **cmat said:**
> Either get a program like Dev-C++ (comes with a Borland compiler I think) and run it under Windows. I think you can cross compile with Mingw but I never used it.

I said I don't have a windows! I hate windows, I don't play much commercial games, I don't need windows. But otherwise I'd compile under windows. (if I had one)

> **danielrmt said:**
> It's the same as gcc.

You won't be able to link your native Linux SDL. You need to download the windows SDL source code and compile the library using MingW32. I can't help very much, but [this tutorial]("http://wiki.wxwidgets.org/Cross-Compiling_Under_Linux") teachs how to do it with wxWidgets. Once you have your compiled windows library, you can link your program using mingw compiler, as you would do with gcc.

EDIT: I believe this link is what you are looking for: [http://www.libsdl.org/extras/win32/cross/README.txt](http://www.libsdl.org/extras/win32/cross/README.txt)

Thanks. That's what I was looking for. But I want to include SDL as static, how to do that then? (even with gcc for Linux)

---

