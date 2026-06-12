---
title: "Problems compiling some source code..."
date: 2008-09-28
forum: New to Ubuntu
---

### Post by Murphy1 on 2008-09-28
Hey guys,
I apologize for my ignorance I'm a brand new Linux user, but I'm quickly becoming a huge fan as I learn more and more! I'm taking a software engineering course and doing a lot of coding with emacs, which I'm finding to be significantly more convenient than booting the hefty Visual Studio on my Windows PC.

Anyways, for a recent homework assignment I have to hack a bunch of source code for a game called [Vulture's Claw]("http://en.wikipedia.org/wiki/Vulture%27s_Eye"). I've downloaded the compressed files and decompressed them into a directory /vultures-2.1.0. Once in that directory, I attempted to compile the game by typing "make home" into the terminal, and according to the professor this should create an executable file in my home directory, however it simply creates two blank directories.

Any idea what's going on or what I'm doing wrong? I haven't touched any of the source yet btw. Thanks in advance!

---

### Post by Murphy1 on 2008-09-28
I'm recieiving a bunch of error messages when I'm trying to compile if this is any help at all. The exact error message:
> make[2]: sdl-config: Command not found
../sys/unix/unixmain.c:18:18: error: SDL.h: No such file or directory
make[2]: *** [unixmain.o] Error 1
make[1]: *** [vultureseye] Error 2
make: *** [nethack-home] Error 2 

Any help is mucho appreciated!:D

---

### Post by alastair on 2008-09-28
SDL is a "direct media layer" - a cross-platform multimedia layer.

[http://www.libsdl.org/](http://www.libsdl.org/)

It looks like you need to install the SDL development libs/headers. Start up your package manager and look for something like "libsdl" and install the "-dev" package.

Might get you further.

Alastair

---

### Post by oldos2er on 2008-09-28
> **Murphy1 said:**
> I'm recieiving a bunch of error messages when I'm trying to compile if this is any help at all. The exact error message:


Any help is mucho appreciated!:D

 Usually there is a README and/or INSTALL file that tell you any dependencies needed. And if you haven't already, you'll need to install the package "build-essential".

---

