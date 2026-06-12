---
title: "SDL and TTF using g++"
date: 2006-08-08
forum: Programming Talk
---

### Post by MoxJet on 2006-08-08
Hello.

I have two questions.

First, is there a sudo apt-get install command for the SDL_TTF library?

Second, how would I write in the terminal to compile with SDL_TTF? Currently I use
g++ -o binary code.cpp -lSDL

Thanks in advance,
Dan

---

### Post by Randomskk on 2006-08-08
For SDL TTF, you can apt-get install:
libsdl-ttf2.0-0
libsdl-ttf2.0-0-dev

or
libsdl-ttf1.2
libsdl-ttf1.2-dev 

depends what version you want.
That way of linking looks fine, not sure if you also need to add -lSDL_TTF

By the way, I found those packages by using this command:
apt-cache search SDL TTF

---

### Post by hod139 on 2006-08-08
> **MoxJet said:**
> 
Second, how would I write in the terminal to compile with SDL_TTF? Currently I use
g++ -o binary code.cpp -lSDL


Use
```
 g++ -o binary code.cpp `sdl-config --cflags --libs`-lSDL_ttf

```

---

