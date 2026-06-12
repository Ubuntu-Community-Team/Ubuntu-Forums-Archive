---
title: "SDL compiling issue with Ubuntu Feisty"
date: 2007-04-30
forum: Programming Talk
---

### Post by Vanaheim on 2007-04-30
Hi all,

well, iv been cracking my head for the hole day with this problem:

yesterday i downloaded the sdl package from their website, compiled and installed it, after that i started to compile SDL Mame, until it gets to this error (the same thing, the same error happens with SDL Hazemd)

Compiling src/osd/sdl/video.c...
src/osd/sdl/video.c: In function ‘sdlvideo_monitor_refresh’:
src/osd/sdl/video.c:244: error: ‘SDL_SysWMinfo’ has no member named ‘subsystem’
src/osd/sdl/video.c:244: error: ‘SDL_SYSWM_X11’ undeclared (first use in this function)
src/osd/sdl/video.c:244: error: (Each undeclared identifier is reported only once
src/osd/sdl/video.c:244: error: for each function it appears in.)
src/osd/sdl/video.c:246: error: ‘SDL_SysWMinfo’ has no member named ‘info’
src/osd/sdl/video.c:248: error: ‘SDL_SysWMinfo’ has no member named ‘info’
src/osd/sdl/video.c:249: error: ‘SDL_SysWMinfo’ has no member named ‘info’
src/osd/sdl/video.c:251: error: ‘SDL_SysWMinfo’ has no member named ‘info’
src/osd/sdl/video.c:256: error: ‘SDL_SysWMinfo’ has no member named ‘info’
make: *** [obj/mamepm/osd/sdl/video.o] Error 1

I tried to install and re-install over and over the SDL packages with synaptic but i just get the same error over and over :( 
this is the info of SDL

- which sdl-config

/usr/bin/sdl-config

- sdl-config --version

1.2.11

- locate libSDL

/usr/lib/libSDL.a
/usr/lib/libSDL.la
/usr/lib/libSDLmain.a
/usr/lib/libSDL.so

- tail config.log

tail: cannot open `config.log' for reading: No such file or directory

This Ubuntu install is very fresh, i toke the last couple of days tweaking it to my likes and installing everything i need to work and multimedia and this is the only problem i have, i don't want to have to re-install everything again :(

If someone can help me, i would be very gratefull!

I just don't know what else to do to solve this problem.

Cheers everyone

---

### Post by hod139 on 2007-05-03
You should be able to install libsdl1.2-dev and use ```
sdl-config --cflags
``` to get the compile time flags and ```
 sdl-config --libs 
``` for the linking flags

---

