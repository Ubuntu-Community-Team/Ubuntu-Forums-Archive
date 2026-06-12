---
title: "trouble setting up MinGW with SDL_gfx for crosscompiling"
date: 2008-11-20
forum: Programming Talk
---

### Post by CC_machine on 2008-11-20
i used this script:
[http://icculus.org/~dolson/sdl/](http://icculus.org/~dolson/sdl/)

i've been compiling with:

i586-mingw32msvc-g++ main.cpp -o cross-bin.exe -lmingw32 -lSDLmain -lSDL -lSDL_image -lSDL_ttf -lSDL_mixer -I /usr/i586-mingw32msvc/include/SDL

however the package is missing SDL_gfx: crucial for my current projecct. I've tried and tried but can't figure out how to install and use it properly. I installed MinGW from the repositories and i'm on Ubuntu 8.04.1.

---

### Post by CC_machine on 2008-11-21
Anybody?

---

### Post by hod139 on 2008-11-21
A quick google search landed me here:
[http://www.gamedev.net/community/forums/topic.asp?topic_id=396932](http://www.gamedev.net/community/forums/topic.asp?topic_id=396932)

Does that help you?

---

