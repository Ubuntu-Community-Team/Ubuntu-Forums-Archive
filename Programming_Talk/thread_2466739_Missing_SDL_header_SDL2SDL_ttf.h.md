---
title: "Missing SDL header: SDL2/SDL_ttf.h"
date: 2021-09-04
forum: Programming Talk
---

### Post by 6&amp;(%3$)* on 2021-09-04
I already ran:

sudo apt-get install libSDL2-ttf-2.0-0

I tried to find the .h file:

pc2@pc:~$ find /usr|grep SDL_ttf.h
pc2@pc:~$ locate SDL_ttf.h
pc2@pc:~$ locate SDL2.h
pc2@pc:~$ locate SDL.h
/home/pc2/Desktop/MAME_Test/Make_MAME/mame/3rdparty/SDL2/include/SDL.h
/home/pc2/Desktop/MAME_Test/Make_MAME/mame/build/generated/includes/SDL2/SDL.h
/usr/include/SDL/SDL.h
pc2@pc:~$ 

In the bigger picture, I'm trying to build the modified MAME here, using the author's provided makefile:

$git clone [https://github.com/M-J-Murray/mame.git](https://github.com/M-J-Murray/mame.git)
$cd mame
$make SUBTARGET=arcade -j8

After a few minutes of work, the build stops with a fatal error: 
#include <SDL2/SDL_ttf.h> ... fatal error: SDL2/SDL_ttf.h: No such file or directory.

Python 3.8.10
Ubuntu 20.04.2 LTS

---

### Post by deadflowr on 2021-09-04
Header files come with the -dev  packages
try
```
sudo apt install libsdl2-ttf-dev
```

---

### Post by 6&amp;(%3$)* on 2021-09-04
Thank you.  The makefile is continuing on now.

---

