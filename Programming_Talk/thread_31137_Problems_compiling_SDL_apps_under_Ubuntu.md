---
title: "Problems compiling SDL apps under Ubuntu"
date: 2005-05-02
forum: Programming Talk
---

### Post by Cynicide on 2005-05-02
I'm looking to learn myself some SDL so I've installed gcc/g++ and their appropriate dev packages.  I've also installed libsdl1.2debian, libsdl1.2-dev and libsdl1.2debian-oss.

I've copied the source code from a tutorial at [http://sol.planet-d.net/gp/ch02.html](http://sol.planet-d.net/gp/ch02.html) into a text file, given it a cpp extension and ran "g++ -o ch01 ch01.cpp".

However it seems to be failing at link time with the following errors.

/tmp/ccOdZTnj.o(.text+0x2d): In function `render()':
: undefined reference to `SDL_LockSurface'
/tmp/ccOdZTnj.o(.text+0x3b): In function `render()':
: undefined reference to `SDL_GetTicks'
/tmp/ccOdZTnj.o(.text+0xec): In function `render()':
: undefined reference to `SDL_UnlockSurface'
/tmp/ccOdZTnj.o(.text+0x119): In function `render()':
: undefined reference to `SDL_UpdateRect'
/tmp/ccOdZTnj.o(.text+0x13c): In function `main':
: undefined reference to `SDL_Init'
/tmp/ccOdZTnj.o(.text+0x145): In function `main':
: undefined reference to `SDL_GetError'
/tmp/ccOdZTnj.o(.text+0x171): In function `main':
: undefined reference to `SDL_Quit'
/tmp/ccOdZTnj.o(.text+0x19a): In function `main':
: undefined reference to `SDL_SetVideoMode'
/tmp/ccOdZTnj.o(.text+0x1ad): In function `main':
: undefined reference to `SDL_GetError'
/tmp/ccOdZTnj.o(.text+0x1e3): In function `main':
: undefined reference to `SDL_PollEvent'
collect2: ld returned 1 exit status

Anyone have any ideas?  It looks like I've got all the libraries installed right.

Thanks

---

### Post by Cynicide on 2005-05-02
Adding -lSDL to the gcc line fixed it if anyone is encountering a similar problem.

Final command line was gcc -lSDL -o ch01 ch01.cpp

---

