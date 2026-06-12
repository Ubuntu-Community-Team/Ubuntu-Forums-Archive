---
title: "SDL2 - Undefined references"
date: 2013-08-19
forum: Packaging and Compiling Programs
---

### Post by Syl4r on 2013-08-19
Hi


I just started using SDL2 (on Ubuntu 13.04 x64) and everything was going fine, until I tried to use SDL_image.


I added this piece of code, for loading images:


```
    SDL_Texture* LoadImage(std::string file)
    {
        SDL_Texture* tex = NULL;
        tex = IMG_LoadTexture(ren, file.c_str());
        if (tex == NULL)
            throw std::runtime_error("Failed to load image: " + file + IMG_GetError());
        return tex;
    }

```

I link with -lSDL2 and -lSDL2_image, and I get this undefined references:


```
    g++  -o "SDL"  ./src/main.o   -lSDL2 -lSDL2_image
    /usr/lib/gcc/x86_64-linux-gnu/4.7/../../../x86_64-linux-gnu/libSDL2_image.so: riferimento non definito a "SDL_malloc"
    /usr/lib/gcc/x86_64-linux-gnu/4.7/../../../x86_64-linux-gnu/libSDL2_image.so: riferimento non definito a "SDL_memcmp"
    /usr/lib/gcc/x86_64-linux-gnu/4.7/../../../x86_64-linux-gnu/libSDL2_image.so: riferimento non definito a "SDL_strncasecmp"
    /usr/lib/gcc/x86_64-linux-gnu/4.7/../../../x86_64-linux-gnu/libSDL2_image.so: riferimento non definito a "SDL_memset"
    /usr/lib/gcc/x86_64-linux-gnu/4.7/../../../x86_64-linux-gnu/libSDL2_image.so: riferimento non definito a "SDL_free"
    /usr/lib/gcc/x86_64-linux-gnu/4.7/../../../x86_64-linux-gnu/libSDL2_image.so: riferimento non definito a "SDL_memcpy"
    /usr/lib/gcc/x86_64-linux-gnu/4.7/../../../x86_64-linux-gnu/libSDL2_image.so: riferimento non definito a "SDL_sscanf"
    /usr/lib/gcc/x86_64-linux-gnu/4.7/../../../x86_64-linux-gnu/libSDL2_image.so: riferimento non definito a "SDL_isspace"
    /usr/lib/gcc/x86_64-linux-gnu/4.7/../../../x86_64-linux-gnu/libSDL2_image.so: riferimento non definito a "SDL_realloc"
    /usr/lib/gcc/x86_64-linux-gnu/4.7/../../../x86_64-linux-gnu/libSDL2_image.so: riferimento non definito a "SDL_strcmp"
    /usr/lib/gcc/x86_64-linux-gnu/4.7/../../../x86_64-linux-gnu/libSDL2_image.so: riferimento non definito a "SDL_strncmp"
    /usr/lib/gcc/x86_64-linux-gnu/4.7/../../../x86_64-linux-gnu/libSDL2_image.so: riferimento non definito a "SDL_snprintf"
    collect2: error: ld returned 1 exit status

```

What am I doing wrong??

---

### Post by steeldriver on 2013-08-19
Try changing the link order

```
g++  -o "SDL"  ./src/main.o   **-lSDL2_image   -lSDL2** 
```

---

### Post by Syl4r on 2013-08-19
Still the same problem :/

---

### Post by mhaggard25 on 2014-02-13
When I'm using Code::Blocks I use this in my linker settings.

right click the project --> select properties --> Project Build Options --> Linker Settings tab --> Other Linker Options --> -lSDLmain -lSDL -lGL -lSDL_image


this makes my program work

---

