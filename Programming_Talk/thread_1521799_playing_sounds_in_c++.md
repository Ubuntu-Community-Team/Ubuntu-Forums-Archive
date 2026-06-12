---
title: "playing sounds in c++"
date: 2010-07-01
forum: Programming Talk
---

### Post by iron_guitarist1987 on 2010-07-01
What is the easiest way to play a sound file using c++?

---

### Post by iron_guitarist1987 on 2010-07-01
What is the easiest way to play a sound file in C++. I don't care what method is used, just an easy way to do it.

---

### Post by dwhitney67 on 2010-07-01
I forgot who it was on this forum, but one of the generous members posted this code before...
```

//
// Requires the use of libSDL_mixer; available from libsdl devel packages
//
// sudo apt-get install libsdl-mixer1.2-dev libsdl1.2-dev
//
// To build:  g++ `sdl-config --cflags --libs` PlayMusic.cpp -lSDL_mixer -o play
//
// To run:  play <file.mp3>
//

#include <SDL/SDL.h>
#include <SDL/SDL_mixer.h>
#include <iostream>

int main(int argc, char** argv)
{
   // Init
   if (SDL_Init(SDL_INIT_AUDIO) != 0)
   {
      std::cerr << "SDL_Init ERROR: " << SDL_GetError() << std::endl;
      return -1;
   }

   // Open Audio device
   if (Mix_OpenAudio(44100, AUDIO_S16SYS, 2, 2048) != 0)
   {
      std::cerr << "Mix_OpenAudio ERROR: " << Mix_GetError() << std::endl;
      return -1;
   }

   // Set Volume
   Mix_VolumeMusic(100);

   // Open Audio File
   Mix_Music* music = Mix_LoadMUS(argv[1]);

   if (music)
   {
      // Start Playback
      if (Mix_PlayMusic(music, 1) == 0)
      {
         unsigned int startTime = SDL_GetTicks();

         // Wait
         while (Mix_PlayingMusic())
         {
            SDL_Delay(1000);
            std::cout << "Time: " << (SDL_GetTicks() - startTime) / 1000 << std::endl;
         }
      }
      else
      {
         std::cerr << "Mix_PlayMusic ERROR: " << Mix_GetError() << std::endl;
      }

      // Free File
      Mix_FreeMusic(music);
      music = 0;
   }
   else
   {
      std::cerr << "Mix_LoadMuS ERROR: " << Mix_GetError() << std::endl;
   }
    
   // End
   Mix_CloseAudio();
}

```
Read the header of the file for instructions on how to build/run the app, which btw only plays MP3 files.

---

### Post by kknd on 2010-07-01
There are many libraries for audio;

GStreamer ( [http://www.gstreamer.net/]("http://www.gstreamer.net/") ) is a high level library that will probably suit your needs. It's not so easy to learn, but it's worth it.

Other libraries: Phonon (good if you're using Qt4) and audiere ( [http://audiere.sourceforge.net/]("http://audiere.sourceforge.net/") ) . 

audiere is the easiest, but it's more limited than GStreamer.

---

### Post by dwhitney67 on 2010-07-01
.

---

### Post by sushiboxdev on 2010-07-01
I would check out CLAM, its a bit more sophisticated than SDL_Mixer, if thats what your going for that is.

[http://clam-project.org/](http://clam-project.org/)

---

### Post by BenAshton24 on 2010-07-01
> **iron_guitarist1987 said:**
> I don't care what method is used, just an easy way to do it.

In that case, how about this:
```
system("mplayer sound.ogg");
```
It's cheating but if you want something simple, it works.

---

