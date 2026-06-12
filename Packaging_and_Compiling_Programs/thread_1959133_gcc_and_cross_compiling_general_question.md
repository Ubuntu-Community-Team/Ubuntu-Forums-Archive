---
title: "gcc and cross compiling general question"
date: 2012-04-15
forum: Packaging and Compiling Programs
---

### Post by compiz addict on 2012-04-15
How?

Following the tutorial on icculus.org/~dolson/sdl/ I have installed mingw32 and the SDL libraries, but I am stumped when it tells me to use ./configure. I don't use an IDE, so I don't have a ./configure file.

I've just been using a compile script that uses g++. Can I add arguments to g++ to accomplish the same thing? How?

---

### Post by compiz addict on 2012-04-15
Update:
I got this working:
```

i586-mingw32msvc-g++ -o stickEngine.exe `/opt/SDL-1.2.13/bin/i586-mingw32msvc-sdl-config --libs` `/opt/SDL-1.2.13/bin/i586-mingw32msvc-sdl-config --cflags` -lSDL_image -lSDL_ttf -lSDL_mixer *.cpp

```

but SDL_ttf.h doesn't exist according to the compiler.
I'm assuming following this tutorial also would have installed SDL_ttf based on the fact that it is in the example "Makefile.mingw" file.

---

