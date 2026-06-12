---
title: "SFML doesn't work on ubuntu."
date: 2022-08-30
forum: New to Ubuntu
---

### Post by tamirluka on 2022-08-30
I have tried to install SFML engine on ubuntu but as i understand it unbuntu can't compatible with win32 api,
windows users can install visual studio and change win64 to win 34 what let them use SFML as it is old fashion gaming engine, is there anything we can do?
THANK YOU VERY MUCH!

---

### Post by QIII on 2022-08-30
It is likely that Ubuntu will have nothing to do with a Win32 API natively because it is Linux, not Windows.

However, you could install the 64 bit version of the latest release of Monodevelop, which should give you the APIs you need for a C# application.  But Monodevelop is 64bit as I recall.

---

### Post by Holger_Gehrke on 2022-08-30
I'm not quite certain what your final goal is. Do you want to compile programs using sfml on Linux for Linux but for the i386 architecture ? Then according to the [download page for sfml]("https://www.sfml-dev.org/download/sfml/2.5.1/") you'll have to compile a 32bit sfml from source and set some options when compiling. Given the fact that Ubuntu is slowly but surely dropping support for 32 bit systems (you can still run 32 bit programs and a lot of libraries are still available from the repositories in 32 bit versions in addition to the default 64 bit versions but you can't install Ubuntu on a 32 bit system), doing so makes little to no sense unless you're writing something that needs to work on some 12+ years old hardware.

Or do you want to compile Windows programs on Linux using sfml ? Then you're getting into real deep wizardry. There are sets of libraries and combinations of compiler settings which make such things possible according to what I've read (mingw is not just for compiling Linux programs on Windows anymore; you can compile with the mingw libraries on Linux and tell the linker to produce PE-files instead of the elf which is default on Linux thereby creating a program that has some chance of running on a Windows machine). Never done it myself, though.

And if it's both you want to do - compile a 32 bit Windows executable on Linux - you'll have to combine a 32 bit sfml with mingw or some other way of producing Windows programs.

Holger

---

### Post by grahammechanical on 2022-08-31
What is the difference between Visual Studio and Visual Studio Code. Both are available for installation on Linux.

[https://visualstudio.microsoft.com/downloads/](https://visualstudio.microsoft.com/downloads/)

The version for use on Ubuntu should have the .deb file extension and not rpm extension.

Visual Studio Code

[https://linuxize.com/post/how-to-install-visual-studio-code-on-ubuntu-20-04/](https://linuxize.com/post/how-to-install-visual-studio-code-on-ubuntu-20-04/)

Regards

---

