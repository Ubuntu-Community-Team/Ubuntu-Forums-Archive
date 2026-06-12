---
title: "where are the SDL libs?"
date: 2006-02-28
forum: Programming Talk
---

### Post by kel on 2006-02-28
hi all, i'm very new to ubuntu/linux so please go easy :D

I've installed eclpise/cdt and also gcc from synaptic, and i am able to run simple programs through eclipse (no idea how to run the binary with linux), but it seems to we working fine. 

I'd like to use SDL, but i have no idea how to install it or what to link to.

I tried downloading SDL-devel-1.2.9-1.i386.rpm from the sdl site but ubuntu didn't like the .rpm file so i didn't get very far there. I then loaded libsdl1.2debian-arts from synaptic hoping this would install all the sdl development files, but i'm left clueless to what its installed and where.

So basically, how do i get and set up sdl and what libs do i need to point the linker to create a simple sdl window.

hope that makes sence, and thanks.

---

### Post by tageiru on 2006-02-28
No need to download it yourself, it is already in the repositories.

Search for libsdl in synaptic, you want the -dev package to link your software with sdl.

---

### Post by kel on 2006-02-28
Ahh, there are a tone of sdl libs in there, which one do i install so I can use sdl to set up a fullscreen or windowed opengl app?

I clicked on libsdl-console-dev and marked it for install but i got this message:

[I]Could not mark packages for installation or upgrade
blah-blah unresolved dependencies... etc.
libsdl-console-dev:
 Depends: libsdl-console but it is not going to be installed
 Depends: libsdl-image1.2-dev  but it is not installable[/I]

i've followed the [https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto) and i think i've set up Synaptic right, but i could be wrong :D

cheers

---

### Post by hod139 on 2006-02-28
```
sudo apt-get install libsdl1.2-dev libsdl1.2debian
``` 
This will install the development libs and the runtime libraries

Then to include SDL into your program, put the following include
```
#include <SDL/SDL.h>
```

---

### Post by kel on 2006-03-01
thanks guys, i think the problem was down to a dodgy ubuntu installation. 

During the final installation process my screen displayed garbage, so i hit the power button hoping it would continue the installation after the reboot, but obviously some important files where missing as i wasn't able to install or even find a lot of things through Synaptic.

anyhoo, i've reinstalled ubuntu and libsdl1.2-dev and loads of other stuff is now available, so although i haven't tested anything yet it seems like i should be ok now.

thanks for the help.

---

### Post by kel on 2006-03-01
Almost there.

I've installed eclipse cdt, and the sdl libs and have writen a small sdl/opengl test app but I'm having trouble compiling it.

The libraries I've linked to are:

SDLmain
SDL
opengl32
glu32

But the opengl lib names seem to be wrong as i get this error in eclipse:

[I]Building target: test
Invoking: GCC C++ Linker
g++ -otest ./Main.o -lSDLmain -lopengl32 -lSDL
/usr/bin/ld: cannot find -lopengl32
collect2: ld returned 1 exit status
make: *** [test] Error 1
make: Target `all' not remade because of errors.
Build complete for project test[/I]

I've had a quick search but carn't find any info.

Thanks

---

### Post by norfenstein on 2006-03-01
I don't think this is your (current) problem, but when I was first [trying](http://ubuntuforums.org/showthread.php?t=5982&highlight=sdl+opengl) this on Ubuntu I had issues because I hadn't installed the development files for my video driver. Assuming you're using nvidia-glx, you'll probably need nvidia-glx-dev installed too.

---

### Post by hod139 on 2006-03-01
The libraries you want to link against are SDL, pthread, GL and GLU. SDL also has a really nice way to get the cflags and the libs directly. In a terminal type:
```

sdl-config --cflags

``` ```

 sdl-config --libs
 
``` 
and the output is the correct includes and libs respectively.

So, if you were writing a makefile, it would look something like:
```

CXX=g++

SDL_CFLAGS := $(shell sdl-config --cflags)
SDL_LDFLAGS := $(shell sdl-config --libs)

CPPFLAGS =  ${SDL_CFLAGS} -g3 -Wall
LDFLAGS =  ${SDL_LDFLAGS} -lGL -lGLU

all: test

test: test.o

clean:
        rm -f *.o test *~


```

---

### Post by kel on 2006-03-01
Cheers hod, all working now, phew, not so bad this Linux lark :)

I just added GL, GLU and pthread to the libs list in eclipse rather than run sdl-config as thankfully eclipse manages the make files for me, which is handy because I've no idea how they work.

btw, whats pthread linked in for?

---

### Post by hod139 on 2006-03-01
I'm not 100% sure.  Maybe SDL's events are multithreaded.  I've always used 
```
sdl-config --libs
``` which links against it.

---

### Post by kel on 2006-03-01
oh yeah, SDL supports threads so maybe its for those, I have no idea if the events are threaded though.

The only problem i have now is that if i use cube maps, all my other textures seem to vanish, oops. But, I'm running on a dell 1300 with an intel GMA 900 so maybe its something to do with that, according to the bios the vid memory is set to 8mb, and there is no way to alter it as dell have locked the options \\:D/ 

I'll wait until Dapper is released before I start digging around for a solution for this though.

Cheers.

---

