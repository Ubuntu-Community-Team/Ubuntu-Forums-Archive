---
title: "Static Linking with SDL"
date: 2009-01-21
forum: Programming Talk
---

### Post by taiji_jian on 2009-01-21
Does anyone know how to static link with SDL in ubuntu? I'm using 

gcc main.c -static -Wall `sdl-config --static-libs --cflags`

and I get a bunch of undefined references like:

main.c:(.text+0x1c): undefined reference to `SDL_Init'
main.c:(.text+0x48): undefined reference to `SDL_Quit'

...

---

