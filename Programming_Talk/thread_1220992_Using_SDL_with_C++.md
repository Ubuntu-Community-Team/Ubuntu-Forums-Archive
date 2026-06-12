---
title: "Using SDL with C++"
date: 2009-07-23
forum: Programming Talk
---

### Post by multiholle on 2009-07-23
I wan't to compile the following program with g++. Using SDL I wan't to play a mp3 file. I installed libsdl-dev and libsdl-mixer-dev. How could I use the libs? 

```
holle@x300:~/cpp$ g++ sound.cpp
/tmp/ccq8XZ82.o: In function `playMP3(char const*)':
sound.cpp:(.text+0x82): undefined reference to `Mix_OpenAudio'
sound.cpp:(.text+0x8d): undefined reference to `Mix_LoadMUS'
sound.cpp:(.text+0x9c): undefined reference to `Mix_VolumeMusic'
sound.cpp:(.text+0xaf): undefined reference to `Mix_PlayMusic'
collect2: ld gab 1 als Ende-Status zurück

``````
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <math.h>
#include <iostream>

#include <SDL/SDL.h>
#include <SDL/SDL_mixer.h>

void playMP3(const char *mp3) {
    Mix_Music *music;
    Mix_OpenAudio(44100, AUDIO_S16SYS, 2, 2048);
    music = Mix_LoadMUS(mp3);
    Mix_VolumeMusic(100);
    Mix_PlayMusic(music, -1);
}

int main() {
    playMP3("/home/holle/test.mp3");
}
```

---

### Post by MadCow108 on 2009-07-23
you need to link against the sdl library.
g++ -lSDL_mixer file.cpp

also the headers you include are C headers not C++ headers (although that won't stop it from working, its bad style).

---

### Post by Sockerdrickan on 2009-07-23
basically [FONT=monospace]
[/FONT]g++ sound.cpp -lSDL_mixer

---

### Post by multiholle on 2009-07-23
> also the headers you include are C headers not C++ headers (although that won't stop it from working, its bad style).     what would be a better style?
```
g++ sound.cpp -o sound -l SDL_mixer
```works. but when I start the program with ```
./sound
``` nothing happens. the program terminates in the moment I started it.

---

### Post by MadCow108 on 2009-07-23
can't help with sdl_mixer as I don't know it.

But in c++ the c headers have no .h and a c infront.
e.g:
instead of
#include <stdio.h>
use:
#include <cstdio>

generally you should avoid using standard c libraries and stick to c++ standard libraries (strings,vectors,streams etc...). Their often easier to use and less error prone.

---

### Post by monraaf on 2009-07-23
You probably have to initialize the sound system first. See SDL_Init. You can use sdl-config to get the compiler and linker flags for the sdl library (e.g. `sdl-config --cflags --libs`)

---

### Post by multiholle on 2009-07-23
Now it works. I have to wait for the music to end playback before closing the program. Is this a better c++ style? What should I do with the includes "SDL/SDL.h,..."?

> You can use sdl-config to get the compiler and linker flags for the sdl library (e.g. `sdl-config --cflags --libs`) 	
What do you mean with this?


```
#include <iostream>
#include <SDL/SDL.h>
#include <SDL/SDL_mixer.h>

using namespace std;

int main() {
    // Init
    if (SDL_Init(SDL_INIT_AUDIO) != 0)
        cout << "SDL_Init ERROR: " << SDL_GetError() << endl;
    else
        cout << "SDL_Init SUCCESS" << endl;

    // Open Audio device
    if (Mix_OpenAudio(44100, AUDIO_S16SYS, 2, 2048) != 0)
        cout << "Mix_OpenAudio ERROR: " << Mix_GetError() << endl;
    else
        cout << "Mix_OpenAudio SUCCESS" << endl;
    
    // Set Volume
    Mix_VolumeMusic(100);
    
    // Open Audio File
    Mix_Music *music;
    music = Mix_LoadMUS("sound.mp3");
    if (music == 0)
        cout << "Mix_LoadMuS ERROR: " << Mix_GetError() << endl;
    else
        cout << "Mix_LoadMus SUCCESS" << endl;
    
    // Start Playback
    if (Mix_PlayMusic(music, 1) != 0)
        cout << "Mix_PlayMusic ERROR: " << Mix_GetError() << endl;
    else
        cout << "Mix_PlayMusic SUCCESS" << endl;
    int startTime = SDL_GetTicks();
        
    // Wait
    while (Mix_PlayingMusic()) {
        SDL_Delay(1000);
        cout << "Time: " << (SDL_GetTicks() - startTime) / 1000 << endl;    
    }    
        
    // Free File
    Mix_FreeMusic(music);
    music = 0;
    
    // End
    Mix_CloseAudio();
    return 0;    
}

```

---

### Post by MadCow108 on 2009-07-23
my comment was just directed at those includes:
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <math.h>
these exist as seperate c++ headers cstdio,cstdlib,cstring and cmath.
the other includes are fine.


sdl-config --cflags --libs
is a tool of sdl that prints the compilerflags (--cflags) and libraries (--libs) needed to compile a program linking with sdl.
it will output something like that:
> sdl-config --cflags --libs
-I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT
-L/usr/lib -lSDL

so
g++ `sdl-config --cflags --libs` file.cpp
will "expand" to:
g++ -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -L/usr/lib -lSDL file.cpp

In your case it won't help as your using sdl_mixer which is not printed by sdl-config.

(A similar tool worth looking at is pkg-config)

---

### Post by multiholle on 2009-07-24
Is it possible to get the playback time and total time of the current playing song from the sdl library?

---

