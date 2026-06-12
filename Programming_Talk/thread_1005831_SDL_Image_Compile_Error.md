---
title: "SDL_Image Compile Error"
date: 2008-12-08
forum: Programming Talk
---

### Post by Phille on 2008-12-08
Hi!

I'm very new here and have some problems with SDL_Image.
I am using the CodeBlocks IDE and I can compile simple SDL applications.

But When I try to change
```
SDL_LoadBMP("cb.bmp");
```
to
```
IMG_Load("cb.bmp");
```
(both should work) I get an error.

The error:

> /usr/lib/libSDL_image.a(IMG_jpg.o)||In function `IMG_InitJPG': |
(.text+0x12)||undefined reference to `jpeg_calc_output_dimensions'|
/usr/lib/libSDL_image.a(IMG_jpg.o)||In function `IMG_InitJPG': |
(.text+0x1c)||undefined reference to `jpeg_CreateDecompress'|
/usr/lib/libSDL_image.a(IMG_jpg.o)||In function `IMG_InitJPG': |
(.text+0x26)||undefined reference to `jpeg_destroy_decompress'|
/usr/lib/libSDL_image.a(IMG_jpg.o)||In function `IMG_InitJPG': |
(.text+0x30)||undefined reference to `jpeg_finish_decompress'|

[...]

||=== Build finished: 30 errors, 0 warnings ===|


Ok... Doesn't say much, does it?
[http://ubuntu-gamedev.wikispaces.com/How-To+Setup+SDL+for+games+development](http://ubuntu-gamedev.wikispaces.com/How-To+Setup+SDL+for+games+development)
Here it says that I need these libs(I got the most of them before):

> libsdl-1.2debian
 libsdl-1.2debian-alsa
 libsdl-1.2dev
 libsdl-image1.2
 libsdl-image1.2-dev
 libsdl-mixer1.2
 libsdl-mixer1.2-dev
 libsdl-net1.2
 libsdl-net1.2-dev

But I couldn't find libsdl-1.2debian and libsdl-1.2debian-alsa. Is that my problem?

I hope somebody can help me.

Phille

PS: I'm still learning English. xD

---

### Post by Phille on 2008-12-08
Mh...
I am laughing right now xD

I just did this:

> g++ sdltest.cpp -o sdltest -lSDL

Now I am smarter.

> g++ sdltest.cpp -o sdltest -lSDL -lSDL_image

Sorry for posting this Thread

---

