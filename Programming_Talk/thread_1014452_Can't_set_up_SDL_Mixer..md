---
title: "Can't set up SDL_Mixer."
date: 2008-12-17
forum: Programming Talk
---

### Post by DOS4dinner on 2008-12-17
Ubuntu 8.04
I'm using Code::Blocks.

I have SDL_Mixer's dev and everything installed in synaptec (Pretty sure, at least--I have green dots by both of the libSDL_mixer files) and Code::blocks appears to have found the header, but I can't seem to use it.

```
#include <string>
#include <vector>
#include <SDL/SDL.h>
#include "SDL/SDL_mixer.h"

nt main ( int argc, char** argv )
{
    printf("begin\n");
    // initialize SDL video
    if ( SDL_Init( SDL_INIT_VIDEO | SDL_INIT_AUDIO) < 0 )
    {
        printf( "Unable to init SDL: %s\n", SDL_GetError() );
        return 1;
    }



    Mix_OpenAudio( MIX_DEFAULT_FREQUENCY, MIX_DEFAULT_FORMAT, 2, 4096);
```

When I try to compile it, it gives me an "Undefined reference to Mix_OpenAudio" error.

I can use normal SDL and SDL_Image just fine. What am I doing wrong?

---

### Post by dwhitney67 on 2008-12-17
> **DOS4dinner said:**
> ...

When I try to compile it, it gives me an "Undefined reference to Mix_OpenAudio" error.

I can use normal SDL and SDL_Image just fine. What am I doing wrong?

"Undefined reference ..." messages are not produced by the compiler; they are produced by the linker.  Basically it is telling you that it (the linker) cannot resolve a library function that you are calling.  You need to tell code::block which library to link in.

I don't use an IDE for development; I prefer to use vim and a Makefile.  Somewhere, you need to convey to code::block to use `sdl-config --libs`.

---

