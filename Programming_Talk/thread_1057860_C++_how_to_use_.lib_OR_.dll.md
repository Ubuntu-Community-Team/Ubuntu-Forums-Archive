---
title: "C++: how to use *.lib OR *.dll"
date: 2009-02-02
forum: Programming Talk
---

### Post by balagosa on 2009-02-02
I have this library file called "inpout32.lib", it is a driver created by one of my professors for inter-action with the parallel port for interfacing. The file also comes in "inpout32.dll"

I have this function:
void _stdcall Out32(short data);
which is in the lib OR dll file which i want to import.

The problem:
I want to write a program using gedit. But I do not know how to use the dll OR lib file. If I had an API/software like Visual Studio, it could have been so easy to include in my project/workspace.

---

### Post by nvteighen on 2009-02-02
Probably, you won't be able to use it as that file is very surely not in a GNU/Linux-compatible format.

What you do is include the header (*.h) and use the functions. Then, in gcc you tell the linker to link your program to that specific library... but again, it has to be in a GNU/Linux-compatible format.

A solution is to ask your professor for the source and recompile that library... (or search for a GNU/Linux-specific library). But, if it's a driver, it may have system-specific (I guess Windows-specific...) stuff that may not be portable.

---

### Post by jespdj on 2009-02-02
*.lib is a statically linked Windows library; *.dll is a dynamically linked Windows library.

Windows programs and libraries do not work on Linux - it's not going to be possible to use those libraries on Linux directly. If you really have to use those libraries, you have no choice but to program on Windows.

On Linux, dynamically linked libraries have the extension *.so (for "shared object").

---

### Post by Ferrat on 2009-02-02
> **jespdj said:**
> *.lib is a statically linked Windows library; *.dll is a dynamically linked Windows library.

Windows programs and libraries do not work on Linux - it's not going to be possible to use those libraries on Linux directly. If you really have to use those libraries, you have no choice but to program on Windows.

On Linux, dynamically linked libraries have the extension *.so (for "shared object").

Well yes and no, he will only be able to compile it for Windows using that lib, "development" is still possible in Linux, you could try it in wine, or just run a virtual machine to test it. 

The idea of asking for the source is the best way to go imo, this way you might be able to make a Linux version, perhaps with the help of the professor introducing him to Linux and getting some creds for the extra work??

---

### Post by balagosa on 2009-02-03
problem is, he is not teaching in the university anymore. So I guess i will have to code in windows then.

BUT I HAVE A BIG QUESTION!

Have you guys ever tried interfacing in Ubuntu, specifically parallel port and USB port. Maybe I can say, making printer software. With your help, I can make my own counter part code for the useless library and dll.

---

### Post by Ferrat on 2009-02-03
> **balagosa said:**
> problem is, he is not teaching in the university anymore. So I guess i will have to code in windows then.

BUT I HAVE A BIG QUESTION!

Have you guys ever tried interfacing in Ubuntu, specifically parallel port and USB port. Maybe I can say, making printer software. With your help, I can make my own counter part code for the useless library and dll.

Well just of the top of my head I know Ubuntu and Linux are mostly open source and I do know that Ubuntu can handle printers so I would guess you could just take a look inside their code for USB or parallel port and see what you need to use :p

---

### Post by balagosa on 2009-02-03
> **Ferrat said:**
> Well just of the top of my head I know Ubuntu and Linux are mostly open source and I do know that Ubuntu can handle printers so I would guess you could just take a look inside their code for USB or parallel port and see what you need to use :p

nice Idea! why did not I think about this. So I guess the right place to look will be at cups-development then.

Anyone can give me a head-start?

---

### Post by nvteighen on 2009-02-03
> **balagosa said:**
> nice Idea! why did not I think about this. So I guess the right place to look will be at cups-development then.

Anyone can give me a head-start?
If you just want something that prints, CUPS is the way. But if you want to control some other device through USB or the parallel port, then CUPS won't help you.

---

### Post by clustermonkey on 2009-02-06
If you are just wanting to toggle the data pins of the
parallel port, try the "parapin" project on Sourceforge.
It is a library that provides functions for the printer
port.

---

