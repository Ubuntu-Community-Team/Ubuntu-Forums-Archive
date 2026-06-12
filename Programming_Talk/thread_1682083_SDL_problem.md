---
title: "SDL problem"
date: 2011-02-05
forum: Programming Talk
---

### Post by dAND3h on 2011-02-05
Hi all. I am tearing my hair out. I have been trying, and failing miserably to get this small SDL project compiling from C::B, and even the terminal. I have installed everything needed for SDL, according to this how-to: [http://ubuntu-gamedev.wikispaces.com/How-To+Setup+SDL+for+games+development](http://ubuntu-gamedev.wikispaces.com/How-To+Setup+SDL+for+games+development) . 

When in C::B, When I create a new SDL project, that compiles fine, everything works! But when I try to compile say, a small demo SDL project that my lecturer gives me, it tells me " SDL.h: No such file or directory". I managed to fix this part inside C::B by adding the include/SDL directory to the project. But, I get segmentation faults all the time! I managed to compile from the terminal aswell, using "g++ -Wall g03-01.cpp -o g03-01 `sdl-config --libs` `sdl-config --cflags`"...but what the hell? It shouldn't be this difficult to do it!

After, I did this, I added the sdl-config --libs to C::B linker settings, and the --libs to the compiler settings. This made no difference, I still receieve segmentation fault. All I seem to be getting with c::b is segmentation faults!

According to that how-to, if I should compile using:
g++ -o test-sdl test-sdl.cpp -lSDL, but that returns the " SDL.h: No such file or directory" error.

I used locate SDL.h, output: /usr/include/SDL/SDL.h
I made sure all the header files that were being used were inside the include folder. Please somebody help me.



EDIT: Ok, This is so damn weird. I  have removed all the build options in codeblocks and now I no longer recieve the no file found. I just get lots of undefined references for TTF_....

EDIT2: I have added the SDL and SDL_ttf to the linker settings using -lSDL and -lSDL_ttf, still receive the same ttf errors. Any help?

---

