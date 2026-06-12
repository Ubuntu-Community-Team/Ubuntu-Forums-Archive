---
title: "Setting intallation to usr/lib during installation"
date: 2011-03-04
forum: Packaging and Compiling Programs
---

### Post by tesseract4d on 2011-03-04
All,

I am using Ubuntu for the first time - working on a project and a rich source of binaries required for the project could only run on linux.

I've been trying to run [this]("http://gpwiki.org/index.php/SDL_mixer:Tutorials:Playing_a_WAV_Sound_File") piece of code to play a .wav file and after numerous hiccups, and hours of frustration I managed to compile it. The only problem now is that when I run it, I get the following error message : 
./play_wav_file: error while loading shared libraries: libSDL_mixer-1.2.so.0: cannot open shared object file: No such file or directory

The SDL_mixer library is installed. The problem as I see it is that, it is installed in the /usr/local/lib directory - whereas ubuntu dy default looks for the library at the /usr/lib directory.
I installed libSDL_mixer the same way I installed the otehr libraries (./configure, make, make install) but it kept getting installed into the /usr/local/lib directory.
So I also tried, ./configure --prefix=/usr/lib but to no avail.
I also tried export PKG_CONFIG_PATH = /usr/local/lib before running the application but I kept getting the same message.

I am looking at a quick fix so that I can move ahead with the project. But if you feel, that I might run into this sort of trouble continuously (i.e. that i am not doing something right) then please explain to me what the problem is.

regards

---

### Post by SevenMachines on 2011-03-04
In my opinion for what its worth :)

* Dont build things from source that you dont have to, most sdl stuff is in the repositories, use it unless you have a compelling reason not to

* If you need to build sdl from source then you *should* install to /usr/local or some other 'local' area. You'll tend to break the system if you install to /usr without being sure what your doing and maintaining it to

It doesnt sound like you're actually wanting to build sdl, but use sdl, in which case you should just remove the manual installs that you've done. For future note, to install to /usr you would do this (don't do it though!:))
```
 $ ./configure --prefix=/usr
```

To run the test program that you link to above is very simple, this is also why you should use repository development packages, its very quick to start doing what you actually want to do instead of setting up your development environment, and then fixing it

##### SDL Test Program #####

* If you havent already (sounds like you have), install the core compiler business
```
$ sudo apt-get install build-essential
```* Install the sdl-mixer development package, which will also install anything else it needs, other sdl things, etc
```
$ sudo apt-get install libsdl-mixer1.2-dev 
```* Take your test program

sdltest.c:
```
#include <SDL.h>
#include <SDL_mixer.h>

int main(int args, char * argv[]) {
    if (SDL_Init(SDL_INIT_VIDEO | SDL_INIT_AUDIO) != 0) {
        fprintf(stderr, "Unable to initialize SDL: %s\n", SDL_GetError());
        return 1;
    }

    int audio_rate = 22050;
    Uint16 audio_format = AUDIO_S16SYS;
    int audio_channels = 2;
    int audio_buffers = 4096;

    if(Mix_OpenAudio(audio_rate, audio_format, audio_channels, audio_buffers) != 0) {
        fprintf(stderr, "Unable to initialize audio: %s\n", Mix_GetError());
        exit(1);
    }
    Mix_Chunk *sound = NULL;

    sound = Mix_LoadWAV("sound.wav");
    if(sound == NULL) {
        fprintf(stderr, "Unable to load WAV file: %s\n", Mix_GetError());
    }

    SDL_Surface *screen;

    screen = SDL_SetVideoMode(320, 240, 0, SDL_ANYFORMAT);
    if (screen == NULL) {
        fprintf(stderr, "Unable to set video mode: %s\n", SDL_GetError());
        return 1;
    }

    int channel;

    channel = Mix_PlayChannel(-1, sound, 0);
    if(channel == -1) {
        fprintf(stderr, "Unable to play WAV file: %s\n", Mix_GetError());
    }

    while(Mix_Playing(channel) != 0);

    Mix_FreeChunk(sound);

    Mix_CloseAudio();
    SDL_Quit();

    return 0;
}
```* And compile it...
```
$ gcc -o sdltest sdltest.c `pkg-config --cflags --libs sdl` -lSDL_mixer
```* Now run it in the same directory as a 'sound.wav' file and get pretty beeps and a little window :)

---

### Post by SevenMachines on 2011-03-04
Just to add, if you *do* need to install sdl to /usr/local then you can point your program (ld anyway) toward it either by..

* Each time you run
```
 $ LD_LIBRARY_PATH=/usr/local/lib ./sdltest
```or
* Make it part of the system search path by default by creating a file something like
/etc/ld.so.conf.d/local.conf:
```
/usr/local/lib
```then run
```
$ sudo ldconfig -v
```this should now work because it now looks in local
```
$ ./sdltest
```

---

### Post by tesseract4d on 2011-03-06
SevenMachines,

thank you very much for allt eh feedback.
Yes - the program works fine.

What i need to know is this.
Why is it that when I Just install a library (by ./configure, make, sudo make install), all libraries get installed into /usr/lib while as SDL_mixer gets installed into /usr/local/lib.

Because if that did not happen then I wouldn't have come across this problem in the first place.

regards'
tesseract

---

### Post by SevenMachines on 2011-03-07
configure --prefix defaults to /usr/local, at least, thats what you'll usually see when you see a configure/make source. why sdl have done it differently i couldnt say.

---

### Post by tesseract4d on 2011-03-08
Hi all,

A slightly different problem - but didn't think it deserved a different thread.
I ran into a different problem.
I wrote my own library to play this file - but for some reason or the other I cannot link it.
and yes, I set the path to link and all thatl

I also tried copying the library to the same directory and it didn't work.

This is the error I get,
error while loading shared libraries: libwavplay.so.1: cannot open shared object file: No such file or directory

thanx

---

