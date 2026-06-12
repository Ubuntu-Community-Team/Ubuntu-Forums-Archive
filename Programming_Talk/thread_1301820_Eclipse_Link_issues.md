---
title: "Eclipse Link issues"
date: 2009-10-26
forum: Programming Talk
---

### Post by carthmen on 2009-10-26
Hello,

  First hello to all.  I am a windows convert, went to Debian about a year ago, and now am using Ubunto.  I used to do alot of programing in Visual C in windows and am now taking up the pen in a Linux environment. 

  My problem is: 

  I am using the SDL development libraries.  I added '/user/include/SDL' to the include paths in the project properties of the eclipse project.  Eclipse seems to find them since it does not give me a error on the line #include "SDL.h" and #include "SDL_opengl.h", however, when i reference a function declared in those libraries it comes up with a "undefined reference to functionx" error.

  Any insight on what I may be missing here.  It might just be that im rusty and am missing somehting obvios to, but this code is unmodified as of yet by me, and supposdely compiles as-is.

Thanks for any help you can provide
Roger

---

### Post by januzi on 2009-10-26
Look for something like: 
Project->Properties->C/C++ Build->Tool Settings->Gcc C linker->Libraries

---

### Post by carthmen on 2009-10-26
Hmm..Didn't seem to change anything.

What i've done is try compiling through the command line using both gcc ang g++
g++ -o test main.cpp GameApp.cpp `sdl-config –libs –cflags` I still get the unreferenced issue there as well.  So it seems its more then just a eclipse setting.

Any thoughts on this..

---

### Post by januzi on 2009-10-26
What does > sdl-config –libs –cflags show in the console ? I think it should be > 
sdl-config --libs --cflags (double -) or You could specify all needed files (-lSDL -lSDL_image ...)

---

### Post by carthmen on 2009-11-03
Sorry I didn't update this thread earlier, but for anyone who may stumble on this, i used the -lSDL option for the linker, solved all the problems.

ex. g++ -o test test.cpp -lSDL

There is a option in the menus for adding linker options, just add the -lSDL there.

---

