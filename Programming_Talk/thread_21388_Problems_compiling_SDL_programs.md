---
title: "Problems compiling SDL programs"
date: 2005-03-21
forum: Programming Talk
---

### Post by bloodroses75 on 2005-03-21
Hello, im a relatively new convert from gentoo linux to ubuntu linux and I am having a problem compiling a SDL game I've been working on since using gentoo. I have not modified the code yet since working w/ gentoo and the program compiled fine on it. However, when i now try to compile it under ubuntu i get this error during compile:

[COLOR=Blue]
sunfire:/home/stuff/shooter $ ./compbatch
./compbatch: line 1: sdl-config: command not found
testshoot.c:1:21: SDL/SDL.h: No such file or directory
In file included from testshoot.c:8:
soundsys.h:4:21: SDL/SDL.h: No such file or directory
[/COLOR]

here is the script for compbatch:

[COLOR=Blue]gcc testshoot.c soundsys.c imgmanip.c -o testshoot `sdl-config --libs --cflags` -lSDL_image -lSDL_ttf[/COLOR]

i am using g++ for the compiler and i have checked through apt-get and it claims libsdl is installed along w/ g++. Does anyone have any suggestions to fix this?

Thank you in advance.

---

### Post by toojays on 2005-03-22
Welcome. I also migrated from Gentoo a couple of months ago, so I know where you're coming from. On Ubuntu, to get the headers for a library, you need to install the corresponding -dev package. For SDL, this is libsdl1.2-dev.

---

### Post by bloodroses75 on 2005-03-22
apt-get'd libsdl1.2-dev, libsdl-image1.2-dev, and libsdl-ttf2.0-dev and now my program compiles fine now.  :mrgreen: 

thank you for the help

---

