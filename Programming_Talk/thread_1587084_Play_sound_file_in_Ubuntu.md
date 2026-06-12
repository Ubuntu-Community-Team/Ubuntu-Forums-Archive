---
title: "Play sound file in Ubuntu"
date: 2010-10-02
forum: Programming Talk
---

### Post by toanhoi on 2010-10-02
Hi everybody.I am writing a program by C in Ubuntu .It plays sound file .Example ,I have a sound file audio.wav and saves in ~Desktop/Sound/audio.wav .I used a function play() but I don't find library of this function.Can you write a function to play this sound file???Thanks you

---

### Post by ibuclaw on 2010-10-03
There are lots of Audio libraries available. SDL may be one of the easier ones to use, but you'll be restricted on what types of format you can play.

example code:
[PHP]
#include <SDL/SDL.h>
#include <SDL/SDL_mixer.h>

Mix_Music *MUSIC_HANDLER = NULL;

int
main()
{
  // Init program environment, parse arguments, etc.
  SDL_Init(SDL_INIT_AUDIO);
  Mix_OpenAudio(22050, AUDIO_S16, 2, 4096);
  // start a thread to handle playing music
  // get file and check it exists
  MUSIC_HANDLER = Mix_LoadMUS(filename);
  Mix_PlayMusic(MUSIC_HANDLER, loops); // loops being number of repeats
  // When song finished / you are done with audio.
  Mix_HaltMusic();
  Mix_FreeMusic(MUSIC_HANDLER);
  MUSIC_HANDLER = NULL;
  // End program
  Mix_CloseAudio();
  SDL_Quit();
}
[/PHP]
Though the above by itself is completely useless. Should give you a rough idea of a possible way.

---

### Post by WitchCraft on 2010-10-03
> **toanhoi said:**
> Hi everybody.I am writing a program by C in Ubuntu .It plays sound file .Example ,I have a sound file audio.wav and saves in ~Desktop/Sound/audio.wav .I used a function play() but I don't find library of this function.Can you write a function to play this sound file???Thanks you

Various possibilities: SDL, OpenAL or system("mplayer mysound.wav");

---

### Post by toanhoi on 2010-10-03
thanks you,but I find error when I play a file which formats .mp3 and command in termilar gcc -o audio1 audio1.c :
audio1.c:(.text+0x11): undefined reference to `SDL_Init'
audio1.c:(.text+0x35): undefined reference to `Mix_OpenAudio'
audio1.c:(.text+0x41): undefined reference to `Mix_LoadMUS'
audio1.c:(.text+0x5b): undefined reference to `Mix_PlayMusic'
audio1.c:(.text+0x60): undefined reference to `Mix_HaltMusic'
audio1.c:(.text+0x6d): undefined reference to `Mix_FreeMusic'
audio1.c:(.text+0x7c): undefined reference to `Mix_CloseAudio'
audio1.c:(.text+0x81): undefined reference to `SDL_Quit'
Can you fix?

---

### Post by ibuclaw on 2010-10-03
> **toanhoi said:**
> 
[NOPARSE]thanks you,but I find error when I play a file which formats .mp3 and command in termilar gcc -o audio1 audio1.c :
audio1.c:(.text+0x11): undefined reference to `SDL_Init'
audio1.c:(.text+0x35): undefined reference to `Mix_OpenAudio'
audio1.c:(.text+0x41): undefined reference to `Mix_LoadMUS'
audio1.c:(.text+0x5b): undefined reference to `Mix_PlayMusic'
audio1.c:(.text+0x60): undefined reference to `Mix_HaltMusic'
audio1.c:(.text+0x6d): undefined reference to `Mix_FreeMusic'
audio1.c:(.text+0x7c): undefined reference to `Mix_CloseAudio'
audio1.c:(.text+0x81): undefined reference to `SDL_Quit'
Can you fix?
[/NOPARSE]

Make sure you link in the SDL libraries...
```
gcc -o audio1 audio.c -lSDL -lSDL_mixer
```

---

### Post by toanhoi on 2010-10-04
thanks.I debug successfull.But I run by command ./audio1 ,I can't head nothing

---

### Post by ibuclaw on 2010-10-04
Can you post the code you are using?

---

### Post by toanhoi on 2010-10-04
#include <SDL/SDL.h>
#include <SDL/SDL_mixer.h>
Mix_Music *MUSIC_HANDLER = NULL;
int
main()
{
  // Init program environment, parse arguments, etc.
  SDL_Init(SDL_INIT_AUDIO);
  Mix_OpenAudio(22050, AUDIO_S16, 2, 4096);
  
  // start a thread to handle playing music
  // get file and check it exists
  MUSIC_HANDLER = Mix_LoadMUS("./a.wav");

  Mix_PlayMusic(MUSIC_HANDLER, 1); // loops being number of repeats
  // When song finished / you are done with audio.
 Mix_HaltMusic();
Mix_FreeMusic(MUSIC_HANDLER);
  MUSIC_HANDLER = NULL;
  // End program
 Mix_CloseAudio();
  SDL_Quit();
}  
File a.wav was save in folder of code. I try to run by your command and ./audio1 but I heard nothing

---

### Post by Zugzwang on 2010-10-05
> **toanhoi said:**
> 
File a.wav was save in folder of code. I try to run by your command and ./audio1 but I heard nothing

Consider adding error handling code to your main method. An example is given on the following page: [http://192.121.234.229/manualer/programering/Tao-doc/Tao.Sdl/Tao.Sdl.SdlMixer.Mix_LoadMUS.html](http://192.121.234.229/manualer/programering/Tao-doc/Tao.Sdl/Tao.Sdl.SdlMixer.Mix_LoadMUS.html)

There, it is checked after loading the file whether that task succeeded. In case of a negative answer, you will obtain an error message. As without this error handling, you do not know what went wrong, you should seriously add such code to all functions you used whose documentation states that they can fail.

---

### Post by ibuclaw on 2010-10-05
> **toanhoi said:**
> 
File a.wav was save in folder of code. I try to run by your command and ./audio1 but I heard nothing
As it seems all you did was copy and paste what I presented, with little insight into actually reading the comments I put, or any care in trying to understand what you are doing, I assume you are not here to learn anything. If you were, you'd have probably seen this little detail I pointed out earlier:
> **ibuclaw said:**
> 
Though the above by itself is completely useless. Should give you a rough idea of a possible way.
If you are wanting to play the whole file uninterrupted, you are going to need at the very least a loop to continually check on the audio state. Of course, with a small delay between checks so that you don't eat up CPU time either.

You should be able to look up how to do this yourself. There's an abundance of information available - if not from the Net, then in the header files provided. (I've even managed to write a simple audio player myself after 15 minutes toying about).

---

