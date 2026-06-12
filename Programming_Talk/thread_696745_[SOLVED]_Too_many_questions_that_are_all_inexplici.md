---
title: "[SOLVED] Too many questions that are all inexplicibly related"
date: 2008-02-14
forum: Programming Talk
---

### Post by Zeotronic on 2008-02-14
Recently... today, a few minutes ago in fact, I decided that I no longer liked Ajunta, my reasons for this are too many to explain, and too few to think of. Anyways, I have decided that instead of Anjuta I would rather compile in Terminal and code in some other, relitively simple IDE. I have seen Code Blocks in recent misadventures that forced me into Windows, and it seems like more than I want, and overall I cant understand it anyways.
I have looked at the numerous threads on this forum that demonstrate how to compile with Terminal, however when I try to do it I suffer errors which from what I can tell, suggest that it isn't including various headers that my program utilizes.
> make main
g++ -g -O2    main.cc   -o main
/tmp/ccjY9NZW.o: In function `__static_initialization_and_destruction_0':
/home/dusk/Projects/KeyValues/src/main.cc:20: undefined reference to `SDL_NumJoysticks'
/tmp/ccjY9NZW.o: In function `Screen_Text(long, long, std::basic_string<char, std::char_traits<char>, std::allocator<char> >, unsigned long)':
/home/dusk/Projects/KeyValues/src/main.cc:183: undefined reference to `SDL_UpperBlit'
/tmp/ccjY9NZW.o: In function `dseInputMaster()':
/home/dusk/Projects/KeyValues/src/main.cc:150: undefined reference to `SDL_PollEvent'
/home/dusk/Projects/KeyValues/src/main.cc:150: undefined reference to `SDL_PollEvent'
/tmp/ccjY9NZW.o: In function `Load_Image(std::basic_string<char, std::char_traits<char>, std::allocator<char> >)':
/home/dusk/Projects/KeyValues/src/main.cc:42: undefined reference to `IMG_Load'
/tmp/ccjY9NZW.o: In function `main':
/home/dusk/Projects/KeyValues/src/main.cc:202: undefined reference to `SDL_Init'
/home/dusk/Projects/KeyValues/src/main.cc:203: undefined reference to `SDL_SetVideoMode'
/home/dusk/Projects/KeyValues/src/main.cc:204: undefined reference to `SDL_WM_SetCaption'
/home/dusk/Projects/KeyValues/src/main.cc:205: undefined reference to `SDL_initFramerate'
/home/dusk/Projects/KeyValues/src/main.cc:207: undefined reference to `SDL_JoystickOpen'
/home/dusk/Projects/KeyValues/src/main.cc:208: undefined reference to `SDL_JoystickOpen'
/home/dusk/Projects/KeyValues/src/main.cc:240: undefined reference to `SDL_Flip'
/home/dusk/Projects/KeyValues/src/main.cc:241: undefined reference to `SDL_framerateDelay'
/home/dusk/Projects/KeyValues/src/main.cc:228: undefined reference to `boxRGBA'
/home/dusk/Projects/KeyValues/src/main.cc:243: undefined reference to `SDL_FreeSurface'
/home/dusk/Projects/KeyValues/src/main.cc:245: undefined reference to `SDL_Quit'
/tmp/ccjY9NZW.o: In function `Load_Image(std::basic_string<char, std::char_traits<char>, std::allocator<char> >)':
/home/dusk/Projects/KeyValues/src/main.cc:44: undefined reference to `SDL_DisplayFormat'
collect2: ld returned 1 exit status
make: *** [main] Error 1
dusk@zeomatrix:~/Projects/KeyValues/src$ 

I had compiled the code before in Anjuta, so I would imagine its all correct.
What IDEs can you reccomend using in conjunction with Terminal, and what am I doing wrong?

---

### Post by Wybiral on 2008-02-14
You have to link to the library. Add "-lSDL" to your compile command.

Also:
```

man gcc

```
Should help

---

### Post by Zeotronic on 2008-02-14
Oh, right, -lSDL and such, that totally slipped my mind, should have figured that went in there somewhere. Ok, now I can compile.

---

### Post by rraj.be on 2008-06-28
I tried with -ISDL 

but the error remains the same

```
raj@raj-desktop:~$ gcc -ISDL /home/raj/c/SDL_PlayMusic.c
/tmp/cc0JzND3.o: In function `main':
SDL_PlayMusic.c:(.text+0x34): undefined reference to `SDL_Init'
SDL_PlayMusic.c:(.text+0x3d): undefined reference to `SDL_GetError'
SDL_PlayMusic.c:(.text+0x7a): undefined reference to `Mix_OpenAudio'
SDL_PlayMusic.c:(.text+0x83): undefined reference to `SDL_GetError'
SDL_PlayMusic.c:(.text+0xab): undefined reference to `Mix_LoadMUS'
SDL_PlayMusic.c:(.text+0xb9): undefined reference to `SDL_GetError'
SDL_PlayMusic.c:(.text+0xf9): undefined reference to `SDL_SetVideoMode'
SDL_PlayMusic.c:(.text+0x107): undefined reference to `SDL_GetError'
SDL_PlayMusic.c:(.text+0x136): undefined reference to `Mix_PlayMusic'
SDL_PlayMusic.c:(.text+0x140): undefined reference to `SDL_GetError'
SDL_PlayMusic.c:(.text+0x16f): undefined reference to `Mix_HookMusicFinished'
SDL_PlayMusic.c:(.text+0x17d): undefined reference to `SDL_Delay'
SDL_PlayMusic.c:(.text+0x18b): undefined reference to `Mix_HaltMusic'
SDL_PlayMusic.c:(.text+0x196): undefined reference to `Mix_FreeMusic'
SDL_PlayMusic.c:(.text+0x19b): undefined reference to `Mix_CloseAudio'
SDL_PlayMusic.c:(.text+0x1a0): undefined reference to `SDL_Quit'
collect2: ld returned 1 exit status
raj@raj-desktop:~$ 

```

Any help please.

---

### Post by geirha on 2008-06-28
```
raj@raj-desktop:~$ gcc -[color=red]I[/color]SDL /home/raj/c/SDL_PlayMusic.c
```
-lSDL with a lowercase l (as in library), not an uppercase I (as in include)

---

### Post by rraj.be on 2008-06-28
This is my o/p

```
raj@raj-desktop:~$ gcc -lSDL /home/raj/c/SDL_PlayMusic.c
/tmp/ccrjkhuc.o: In function `main':
SDL_PlayMusic.c:(.text+0x7a): undefined reference to `Mix_OpenAudio'
SDL_PlayMusic.c:(.text+0xab): undefined reference to `Mix_LoadMUS'
SDL_PlayMusic.c:(.text+0x136): undefined reference to `Mix_PlayMusic'
SDL_PlayMusic.c:(.text+0x16f): undefined reference to `Mix_HookMusicFinished'
SDL_PlayMusic.c:(.text+0x18b): undefined reference to `Mix_HaltMusic'
SDL_PlayMusic.c:(.text+0x196): undefined reference to `Mix_FreeMusic'
SDL_PlayMusic.c:(.text+0x19b): undefined reference to `Mix_CloseAudio'
collect2: ld returned 1 exit status
raj@raj-desktop:~$ 


```

---

### Post by geirha on 2008-06-28
Given the names of those functions, you probably need the SDL_mixer library as well. [http://www.libsdl.org/projects/SDL_mixer/](http://www.libsdl.org/projects/SDL_mixer/)

---

### Post by rraj.be on 2008-06-28
Could you please give me command to install that.

But i have installed libstd-mixer1.2 already through my synaptic.

---

### Post by geirha on 2008-06-28
Try linking with SDL_mixer then, by adding "-lSDL_mixer" to your gcc-line.

---

### Post by rraj.be on 2008-06-28
> **geirha said:**
> Try linking with SDL_mixer then, by adding "-lSDL_mixer" to your gcc-line.

That was solved but its getting a new error when i tried to run

```
XDM authorization key matches an existing client!Unable to initialize SDL: Couldn't open X11 display
```

see here

[http://ubuntuforums.org/showthread.php?t=843468](http://ubuntuforums.org/showthread.php?t=843468)

---

