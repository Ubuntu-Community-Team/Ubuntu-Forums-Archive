---
title: "sdl linking hell"
date: 2012-01-14
forum: Programming Talk
---

### Post by neo_marz on 2012-01-14
hi don't know if I'm at the right forum, used google up the ***, tried as hard as I could for a week to figure this out but I'm at my wits end. I'm compiling a program that uses many sdl and sdl_mixer functions and I've linked with sdl in all the various right ways for ubuntu (getting the packages, doing -lSDL -lSDL_mixer -lSDLmain, then trying 'sdl-config --libs') and nothings working, I know that they must be linked against because the linker doesn't complain that it can't find them, however, when I run g++ it complains undefined references to everything as if I linked to nothing at all ( undef reference to Mix_LoadWAV_RW, SDL_Delay, SDL_Init etc...) I installed the packages libsd1.2-dev, and libsdl-mixer1.2/libsdl-mixer1.2-dev and so wtf my mind is boggled. all the includes worked I compiled object files for my prog, I just can't link anything together because I dunno!

If I'm in the wrong place/forum please let me know where I should go for this, thank you.

---

### Post by SevenMachines on 2012-01-15
You'd need to post more specifics of your code, commands, and output to know but as a first guess, are you putting the linking stuff after your source in the compile command? This is required by default these days.

For example, using this simple sdl example.
```
$ cat sdl-test.c 
#include <SDL.h>

int main(int argc, char* argv[])
{
    SDL_Init(SDL_INIT_VIDEO);
    SDL_Quit();
    return 0;
}

# This will fail, libs before source
$ gcc `pkg-config --cflags --libs sdl`  -o sdl-test sdl-test.c 
/tmp/ccL2tGQg.o: In function `main':
sdl-test.c:(.text+0x15): undefined reference to `SDL_Init'
sdl-test.c:(.text+0x1a): undefined reference to `SDL_Quit'
collect2: ld returned 1 exit status

# Success if libs after though
$ gcc -o sdl-test sdl-test.c  `pkg-config --cflags --libs sdl`       
```

---

### Post by ahso4271 on 2012-01-15
works fine for me i only remember such problems on OSX...make sure to not mix that! on Linux you dont need to do unusual stuff alike osx

---

### Post by neo_marz on 2012-01-15
> **SevenMachines said:**
> You'd need to post more specifics of your code, commands, and output to know but as a first guess, are you putting the linking stuff after your source in the compile command? This is required by default these days.

For example, using this simple sdl example.
```
$ cat sdl-test.c 
#include <SDL.h>

int main(int argc, char* argv[])
{
    SDL_Init(SDL_INIT_VIDEO);
    SDL_Quit();
    return 0;
}

# This will fail, libs before source
$ gcc `pkg-config --cflags --libs sdl`  -o sdl-test sdl-test.c 
/tmp/ccL2tGQg.o: In function `main':
sdl-test.c:(.text+0x15): undefined reference to `SDL_Init'
sdl-test.c:(.text+0x1a): undefined reference to `SDL_Quit'
collect2: ld returned 1 exit status

# Success if libs after though
$ gcc -o sdl-test sdl-test.c  `pkg-config --cflags --libs sdl`       
```
ok so I think maybe we're  getting somewhere... when I put in the command
 g++ -o ../prog  first.o second.o third.o (etc.o) `pkg-config --libs sdl`
It still complains but not as much, and I think it stops complaining about the plain sdl functions it's now just complaining about sdl_mixer functions in the 2-3 of the object files.. is there something else I'm missing? maybe I didn't make it clear I'm using sdl as well as sdl_mixer functions/classes.

---

### Post by neo_marz on 2012-01-15
OMG that was it! thank you soo much SevenMachines! I typed in -lSDL -lSDLmain -lSDL_mixer and that made it work too, I'm guessing there was an extra parameter for the pkg-config command I didn't put.
So it's standard to link the libs after the source? is that true for any os? (or most of them) or more specifically, is it true for windows and mac?

---

### Post by t1497f35 on 2012-01-16
No, it's only for Linux (gcc/g++)
Ubuntu is just following suit since it was decided to do so upstream (debian, red hat).
More info [here]("https://wiki.ubuntu.com/NattyNarwhal/ToolchainTransition"), it was planned for Natty but didn't make it in time so it was actually implemented in Oneiric, so the statements in that document about Natty doing the transition aren't really true.
Many people have been caught unaware of this including you and me, but it's nobody to blame obviously.

---

### Post by SevenMachines on 2012-01-16
> **neo_marz said:**
> OMG that was it! thank you soo much SevenMachines! I typed in -lSDL -lSDLmain -lSDL_mixer and that made it work too, I'm guessing there was an extra parameter for the pkg-config command I didn't put.
Yep, sdl-mixer is not part of sdl core. If you were looking for the pkg-config params to use this is what I would do,
```
~$ pkg-config --list-all |grep -i sdl
SDL_mixer                           SDL_mixer - mixer library for Simple DirectMedia Layer
sdl                                 sdl - Simple DirectMedia Layer is a cross-platform multimedia library designed to provide low level access to audio, keyboard, mouse, joystick, 3D hardware via OpenGL, and 2D video framebuffer.
SDL_net                             SDL_net - net library for Simple DirectMedia Layer

$ pkg-config --cflags --libs sdl SDL_mixer
-D_GNU_SOURCE=1 -D_REENTRANT -I/usr/include/SDL  -lSDL_mixer -lSDL  
```> So it's standard to link the libs after the source? is that true for any os? (or most of them) or more specifically, is it true for windows and mac?As mentioned above, its a gcc thing. This is a good explananation of why and how and what
[http://www.gentoo.org/proj/en/qa/asneeded.xml](http://www.gentoo.org/proj/en/qa/asneeded.xml)

---

### Post by neo_marz on 2012-01-16
> **t1497f35 said:**
> No, it's only for Linux (gcc/g++)
Ubuntu is just following suit since it was decided to do so upstream (debian, red hat).
More info [here]("https://wiki.ubuntu.com/NattyNarwhal/ToolchainTransition"), it was planned for Natty but didn't make it in time so it was actually implemented in Oneiric, so the statements in that document about Natty doing the transition aren't really true.
Many people have been caught unaware of this including you and me, but it's nobody to blame obviously.
I see. At least now I know.

---

