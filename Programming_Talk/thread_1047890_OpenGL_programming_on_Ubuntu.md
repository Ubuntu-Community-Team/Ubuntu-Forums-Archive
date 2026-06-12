---
title: "OpenGL programming on Ubuntu"
date: 2009-01-22
forum: Programming Talk
---

### Post by prasath_amd on 2009-01-22
Hi everyone, I am new to using/programming on linux, have been using WinXP for 5yrs, I use the VC++ 2008 Express IDE on Windows. I came to know tat GCC is the compiler of choice for linux, anyway i need clear, detailed advise on compiling & developing C/C++ Based-OpenGL programs on ubuntu. I am poking around ubuntu for the last 6days without getting anything working, I am nearly depressed plz help.

_Five Questions:-_
[B]
1.How Can I set the environment variables for ubuntu & GCC?

2.Where can i get the OpenGL headers, libraries for ubuntu?

3.How to setup my dev environment under ubuntu? ( header/library file dirs )

4.How to compile simple GLUT-Based OpenGL Programs under ubuntu?

5.How to compile full-blown X11-Native windowing-based OpenGL programs on ubuntu?[/B]

I thought SDL would be great on linux, but in their linux-downloads section there are only RPM-packages, where are the .DEB packages?

I'd be very very thankful & happy if u can help me out atleast with some questions. 

Thank You very much for your help in advance.

---

### Post by stroyan on 2009-01-22
[LIST=1]
[*]Environment variables are set in a shell with "export name=value".  They are not system-wide.  They are only inherited by child processes.  If you want them to be set for all logins you could set them in /etc/environment.  That file is  sourced by gdm.
[*]Use the apt-get command to get them.  "sudo apt-get install freeglut3-dev libglew1.5-dev"  Those have dependencies that will bring in packages like libgl-dev and libglu-dev.
[*]"sudo apt-get install build essential" will get gcc and make.  Various packages have "*-dev" and "*-doc" packages for header files and documentation.
[*]"cc -g -o example example.c -lglut -lGL -lGLEW"
[*]Programs that use libX11 directly can be linked the same way as programs that use glut.  Or you could drop linking with glut and list only the X11 libraries directly.  You would want -lX11 and -lXext.
[/LIST]
SDL is available for ubuntu using "sudo apt-get install libsdl1.2-dev".

---

### Post by prasath_amd on 2009-01-23
Thank U so much stroyan, thank u. It really helped me a lot. Man Linux is challenging & equally interesting. :D :D

---

### Post by jespdj on 2009-01-23
> **stroyan said:**
> 
"sudo apt-get install build essential" will get gcc and make.  Various packages have "*-dev" and "*-doc" packages for header files and documentation.
Note it's **build-essential**, not build <space> essential.
> "cc -g -o example example.c -lglut -lGL -lGLEW"
Use **gcc** instead of cc.

---

