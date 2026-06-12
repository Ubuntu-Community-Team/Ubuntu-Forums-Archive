---
title: "help Installing wolf4SDL"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by cosine352 on 2008-08-28
Do anyone know how to install this game?

[http://gaming.gwos.org/doku.php/games:alphabetical:w:wolf4sdl](http://gaming.gwos.org/doku.php/games:alphabetical:w:wolf4sdl)

---

### Post by halitech on 2008-08-28
lots of games on there, can you be a little more specific as to which game you are referring to?

---

### Post by cosine352 on 2008-08-28
I have corrected the link
[http://gaming.gwos.org/doku.php/games:alphabetical:w:wolf4sdl](http://gaming.gwos.org/doku.php/games:alphabetical:w:wolf4sdl)

---

### Post by halitech on 2008-08-28
first thing I found after downloading the source file was I needed SDL_mixer ([http://www.libsdl.org/projects/SDL_mixer/](http://www.libsdl.org/projects/SDL_mixer/)) so I downloaded [http://www.libsdl.org/projects/SDL_mixer/release/SDL_mixer-1.2.8.tar.gz](http://www.libsdl.org/projects/SDL_mixer/release/SDL_mixer-1.2.8.tar.gz) and extracted it then ran
```
./configure
make
suo make install
``` in a terminal
then changed back to the directory where I had the game files and ran make but got errors.  here is what I got
```

daryl@ubuntu:~/Downloads/wolf_linux/Wolf4SDL-1.5-src$ make
===> CXX id_sd.cpp
id_sd.cpp:31:23: error: SDL_mixer.h: No such file or directory
id_sd.cpp:65: error: expected initializer before &#8216;*&#8217; token
id_sd.cpp:68: error: &#8216;MIX_CHANNELS&#8217; was not declared in this scope
id_sd.cpp: In function &#8216;void SD_StopDigitized()&#8217;:
id_sd.cpp:489: error: &#8216;Mix_HaltChannel&#8217; was not declared in this scope
id_sd.cpp: In function &#8216;int SD_GetChannelForDigi(int)&#8217;:
id_sd.cpp:498: error: &#8216;Mix_GroupAvailable&#8217; was not declared in this scope
id_sd.cpp:499: error: &#8216;Mix_GroupOldest&#8217; was not declared in this scope
id_sd.cpp: In function &#8216;void SD_SetPosition(int, int, int)&#8217;:
id_sd.cpp:516: error: &#8216;Mix_SetPanning&#8217; was not declared in this scope
id_sd.cpp: In function &#8216;void SD_PrepareSound(int)&#8217;:
id_sd.cpp:576: error: &#8216;SoundChunks&#8217; was not declared in this scope
id_sd.cpp:577: error: &#8216;Mix_LoadWAV_RW&#8217; was not declared in this scope
id_sd.cpp: In function &#8216;int SD_PlayDigitized(word, int, int)&#8217;:
id_sd.cpp:593: error: &#8216;Mix_Chunk&#8217; was not declared in this scope
id_sd.cpp:593: error: &#8216;sample&#8217; was not declared in this scope
id_sd.cpp:593: error: &#8216;SoundChunks&#8217; was not declared in this scope
id_sd.cpp:600: error: &#8216;Mix_PlayChannel&#8217; was not declared in this scope
id_sd.cpp:602: error: &#8216;Mix_GetError&#8217; was not declared in this scope
id_sd.cpp: In function &#8216;void SD_Startup()&#8217;:
id_sd.cpp:1049: error: &#8216;Mix_OpenAudio&#8217; was not declared in this scope
id_sd.cpp:1051: error: &#8216;Mix_GetError&#8217; was not declared in this scope
id_sd.cpp:1055: error: &#8216;Mix_ReserveChannels&#8217; was not declared in this scope
id_sd.cpp:1056: error: &#8216;MIX_CHANNELS&#8217; was not declared in this scope
id_sd.cpp:1056: error: &#8216;Mix_GroupChannels&#8217; was not declared in this scope
id_sd.cpp:1073: error: &#8216;Mix_HookMusic&#8217; was not declared in this scope
id_sd.cpp:1074: error: &#8216;Mix_ChannelFinished&#8217; was not declared in this scope
id_sd.cpp: In function &#8216;void SD_Shutdown()&#8217;:
id_sd.cpp:1105: error: &#8216;SoundChunks&#8217; was not declared in this scope
id_sd.cpp:1105: error: &#8216;Mix_FreeChunk&#8217; was not declared in this scope
make: *** [id_sd.o] Error 1
daryl@ubuntu:~/Downloads/wolf_linux/Wolf4SDL-1.5-src$ 

```

seeing as how they have no install guide and the readme file is pretty much useless, I'm not sure what we need to do from this step

---

### Post by nicedude on 2008-08-28
From what I see in halitech's outputs I don't think it even remotely looks worth it to mess with that game since there is no install guide and it requires you do install from source that also doesn't like to be installed apparently.

Why not try one of these games that you can get to work much easier, and all of them are 3d first person shooters with much better graphics than circa 1990's wolf 3d

Each of these is in the repositories so they are easy to install

alien arena

nexuiz

warsow

---

### Post by cosine352 on 2008-08-28
Thanks a lot friends. I will try the other games.

---

