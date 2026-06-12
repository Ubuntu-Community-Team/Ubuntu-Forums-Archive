---
title: "HOWTO: Setting Up SDL for Beginners in Games Development"
date: 2006-11-22
forum: Programming Talk
---

### Post by Mickeysofine1972 on 2006-11-22
NOTE: This how to assumes you have already installed build-essential and g++ etc, and that you know how to program in C++. This is not C/C++ tutorial BTW.



Welcome to the first in hopfully many Ubuntu games development HOWTO's. This first one will cover how to setup Simple DirectMedia Layer (SDL), which is a excellent starting point for anyone wanting to get into Games development on the Ubuntu/Linux.

The first thing you need is to install the SDL libraries as well as the development libraries.

So open up your favourite package manager and search for SDL; this should list all the SDL support/development libraries. Now all you need to do is select the following:

libsdl-1.2debian
libsdl-1.2debian-alsa
libsdl-1.2debian-oss
libsdl-1.2dev
libsdl-image1.2
libsdl-image1.2-dev
libsdl-mixer1.2
libsdl-mixer1.2-dev
libsdl-net1.2
libsdl-net1.2-dev

If your doing OpenGL stuff you will also need:
mesa-common-dev
libglu1-mesa-dev

Now you can click 'Apply' and the package manager will download and install your lovely new libraries!

Next we need to test if it works, so we need a simple program:

```

#include "SDL.h"

int main( int argc, char* argv[])
{
	// Fire up SDL, this starts all subsystems; audio video etc.
	
        if ( SDL_Init(SDL_INIT_EVERYTHING) < 0 ) {
            fprintf(stderr, "Unable to init SDL: %s\n", SDL_GetError());
            exit(1); 
        }
	// Now Shut it down
	atexit(SDL_Quit);

	return 0;
}

```

save this into a file called test-sdl.cpp then open a terminal and go to the folder you saved test.cpp in and execute the following commands:

```

g++ `sdl-config --cflags --libs` -o test-sdl test-sdl.cpp
./test-sdl

```

If the program executes and gives no errors! the test was successful.

If NOT then you need to check/reinstall all the libraries and your compiler.

To test the OpenGL stuff you can download a SDL version of glxgears from the SDL website here: 
[http://www.libsdl.org/opengl/SDLgears-1.0.2.tar.gz](http://www.libsdl.org/opengl/SDLgears-1.0.2.tar.gz)

download and unpack then go to the folder in your terminal and type the following:
```

./configure
make
./SDLgears

```

You should see an SDL version of the gxlgears program whizzing round on the screen ;-)

Well, thats it for the first HOWTO, I hope this was a good start and I hope that you might like to contribute if you have any comments or tutorials to add.

Mike

---

### Post by hod139 on 2006-11-22
There is one big mistake in your tutorial, when using SDL you should be including it as:
```
#include "SDL.h"
```**not**
```
#include "SDL/SDL.h"
```and then when building, you should be typing
```

g++ `sdl-config --cflags --libs` -o test-sdl test-sdl.cpp
./test-sdl 

```Another mistake, is that you should be using 
```
atexit(SDL_Quit)
```to guarantee that the library shutdown procedure is called, even when your application fails unexpectedly.

Less important, you shouldn't be initializing SDL using everything when you are not using it, that only slows things down.   You should also be checking the return calls of the SDL functions to see if they actually succeeded.

Also, this tutorial doesn't really do anything, so I have added slightly to it (including the fixes I mentioned above):
```

#include <cstdlib>
#include "SDL.h"

int main( int argc, char* argv[])
{
    // Initialize SDL, using only the video library.
    if ( SDL_Init(SDL_INIT_VIDEO) < 0 ) {
        fprintf(stderr, "Unable to init SDL: %s\n", SDL_GetError());
            exit(1); 
    }
    atexit(SDL_Quit); //clean up the library when you are done with it.
    
    // Create a screen surface, and set the video mode 
    SDL_Surface *screen;
    screen = SDL_SetVideoMode(640, 480, 16, SDL_SWSURFACE);
    if ( screen == NULL ) {
       fprintf(stderr, "Unable to set 640x480 video: %s\n", SDL_GetError());
       exit(1);
    }

    SDL_Event event;
    bool running = true;
    // Loop forever, waiting for the user to quit
    while(running){
       while ( SDL_PollEvent(&event) ) {
          switch (event.type) {
             case SDL_KEYDOWN:
             case SDL_KEYUP:
                if (event.key.type == SDL_KEYUP)
                   printf("RELEASED: ");
                else
                   printf("PRESSED: ");
                 printf( "%s\n", SDL_GetKeyName(event.key.keysym.sym));
             break;
             case SDL_MOUSEMOTION:
                printf("Mouse moved by %d,%d to (%d,%d)\n", 
                    event.motion.xrel, event.motion.yrel, event.motion.x, event.motion.y);
              break;
              case SDL_MOUSEBUTTONDOWN:
                   printf("Mouse button %d pressed at (%d,%d)\n",
                       event.button.button, event.button.x, event.button.y);
               break;
               case SDL_QUIT:
                  running = false;
               }
           }
        }

    return 0;
}

```Again, to compile and run type:
```

g++ `sdl-config --cflags --libs` -o test-sdl test-sdl.cpp
./test-sdl 

```

---

### Post by Mickeysofine1972 on 2006-11-22
Good stuff!

It nice to see people getting involved.

BTW please read the title of the thread again as you might have missed the point of the HOWTO.

Thanks for the example program and I hope you keep contributing.:-D 

Mike

P.S. I have seen programs using SDL.h and SDL/SDL.h in both and haven't seen any major differences in their performance when compiled

---

### Post by hod139 on 2006-11-22
> **Mickeysofine1972 said:**
> 
BTW please read the title of the thread again as you might have missed the point of the HOWTO.

Read it again, what did I miss?

> 
Thanks for the example program and I hope you keep contributing.:-D 

Time allowing I'll contribute as much as I can.

> 
P.S. I have seen programs using SDL.h and SDL/SDL.h in both and haven't seen any major differences in their performance when compiled
The issue is not performance, but portability.

---

### Post by Mickeysofine1972 on 2006-11-22
Ok I Concede to your high godlike knowledge of SDL but lets keep it simple for the sake of the beginners reading this 'Setting Up SDL for Beginners in Games Development'

I really don't want this getting too complex on a HOWTO number one. I did make this deliberately excluding a lot of stuff for the sake of ease of learning the basics.

BTW if you have a HOWTO of your own, I and all the other guys trying to learn would love to read it.

Mike

NOTE OTHER READERS: I plan to cover the input processing contained in the extra program provided by our friend in a later HOWTO or maybe you could do that one hod139?

---

### Post by hod139 on 2006-11-22
> **Mickeysofine1972 said:**
> Ok I Concede to your high godlike knowledge of SDL but lets keep it simple for the sake of the beginners reading this 'Setting Up SDL for Beginners in Games Development'

I really don't want this getting too complex on a HOWTO number one. I did make this deliberately excluding a lot of stuff for the sake of ease of learning the basics.

BTW if you have a HOWTO of your own, I and all the other guys trying to learn would love to read it.

Mike

NOTE OTHER READERS: I plan to cover the input processing contained in the extra program provided by our friend in a later HOWTO or maybe you could do that one hod139?
I wish I could claim godlike knowledge :).  Now I at least understand what you are doing; if you wish to discuss the event loop at a later time this is fine.  I just find that tutorials that don't do anything tend to get ignored by users.  **However**, I still stand by my other comments (using pkg-config, atexit, and checking SDL error messages), if you are going to write tutorials, make sure you teach good habits early.

---

### Post by hod139 on 2006-11-22
Also, check out: [http://www.libsdl.org/intro.en/toc.html](http://www.libsdl.org/intro.en/toc.html)
which contains a very decent introduction.

Here is there introduction code
```

[COLOR=#0000ff]#include[/COLOR] <stdlib.h>
[COLOR=#0000ff]#include[/COLOR] "[COLOR=#000000]SDL.h[/COLOR]"

main([COLOR=#008000]int[/COLOR] argc, [COLOR=#008000]char *[/COLOR]argv[])
{
    [COLOR=#0000ff]if[/COLOR] ( SDL_Init(SDL_INIT_AUDIO|SDL_INIT_VIDEO) < 0 ) {
        fprintf(stderr, "[COLOR=#000000]Unable to init SDL: %s\n[/COLOR]", SDL_GetError());
        exit(1);
    }
    atexit(SDL_Quit);

    ...
}

``` 
As you can see, they use:
```

[COLOR=#0000ff]#include[/COLOR] "[COLOR=#000000]SDL.h[/COLOR]" 
```, they check the return value of SDL_Init, and they use atexit.  These habits need to be taught at the earliest stage of the tutorials if you want to keep writing them.

---

### Post by Mickeysofine1972 on 2006-11-22
Adjusted to suite

Mike

---

### Post by Mickeysofine1972 on 2006-11-22
I'd just like to say that I am really pleased with response from you guys

Keep up the good work! and keep contributing!

We could have a game in the offing!

Mike

---

### Post by Choad on 2006-11-23
nice work

---

### Post by Mickeysofine1972 on 2006-11-24
we aim to please ;-)


Mike

---

### Post by Mickeysofine1972 on 2006-11-24
Added new info on howto setup OpenGL as well

Mike

---

### Post by VDM on 2006-11-24
What would be nice is to make a howto that...

a) loads a model from a file (blender?) and display it in SDL/OpenGL.

b) For the 2D scene. A simple map where you can scroll around on.

c) A simple jumper concept. 

Not sure if C is doable in a simple howto though. Options A & B sure are. 
Hopefully they entice new people in making simple (but fun) games. :mrgreen:

They could include, setting title / icons, handling images (depth, scaling, transparancy), pixel fun?
Maybe making some form of a state machine? SDL_Image sure makes things handy when it comes to images.
Just some ideas ...

Nice initiative!

---

### Post by Mickeysofine1972 on 2006-11-24
Thanks for contributing!

Yes your absolutely right and we will be writing a & b in due course.

About, c though? can you explain what you mean? I don't understand what your saying there.

Great stuff glad we have helped!

Mike

---

### Post by VDM on 2006-11-24
With "Jumper" i ment the games like Mario, Supertux, Jack Rabbit, Mega Man.. you get the picture ;)

---

### Post by Mickeysofine1972 on 2006-11-24
Yeah I agree on that too ;-)

Understood and I will begin planning ASAP

If you or any other readers have any comments or contributions please let us know

Mike

---

### Post by amo-ej1 on 2006-11-24
particle systems are also nice examples.

---

### Post by Mickeysofine1972 on 2006-11-24
That a good one

Keep 'em coming!

Mike

---

### Post by VDM on 2006-11-24
Actually,.. i might have an old project thingy of me laying around. It is a 2D scrolling thingy that after pressing ESC, has 2 "mobiles" on a map that can be moved around. You can scroll around, toggle tiles from "gras" to "water". scrolling by mouse_close_to_edge is also in there. There is even some form of comments here and there :)

I havn't looked at it for ages and is probably full of bugs and crappy implementations, but it might help you a bit. Note: Any comments and remarks should not be taken seriously :mrgreen: 

You can download it from [here]("http://zilx.sytes.net/~vdm/gototalwar.14-8-05.tar.gz").

When you do the ./configure foo, make sure to add -lSDL_image to the Makefile.
Also move the ./src/gototalwar binary to /debug/src/. This is because all resource material is located there and it will segfault without.

When you build it with kdevelop, everything should be ok.
No warrenties whatsover!! =)

---

### Post by kthakore on 2006-11-27
I tried to install sdl-dev files and I followed a series of errors and failed atempts what should I do

>  sudo apt-get install libsdl1.2debian libsdl1.2debian-all libsdl-image1.2 libsdl-image1.2-dev libsdl-mixer1.2 libsdl-mixer1.2-dev libsdl-net1.2 libsdl-net1.2-dev freeglut3 freeglut3-dbg freeglut3-devReading package lists... Done
Building dependency tree       
Reading state information... Done
libsdl1.2debian is already the newest version.
libsdl-image1.2 is already the newest version.
libsdl-mixer1.2 is already the newest version.
libsdl-net1.2 is already the newest version.
freeglut3 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  freeglut3-dev: Depends: xlibmesa-gl-dev but it is not going to be installed or
                          mesag-dev or
                          libgl-dev
                 Depends: xlibmesa-glu-dev but it is not installable or
                          libglu-dev
  libsdl-image1.2-dev: Depends: libsdl1.2-dev (>= 1.2.10) but it is not going to be installed
  libsdl-mixer1.2-dev: Depends: libsdl1.2-dev (>= 1.2.4) but it is not going to be installed
                       Depends: libsmpeg-dev (>= 0.4.4-7) but it is not going to be installed
  libsdl-net1.2-dev: Depends: libsdl1.2-dev (>= 1.2.5) but it is not going to be installed
E: Broken packages
admin@KAYNOOK:~$ sudo apt-get install lisdl1.2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package lisdl1.2-dev
admin@KAYNOOK:~$ sudo apt-get install libsdl1.2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  libsdl1.2-dev: Depends: libglu1-mesa-dev but it is not going to be installed or
                          libglu-dev
E: Broken packages
admin@KAYNOOK:~$ sudo apt-get install libglu-dev libsdl1.2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libglu1-mesa-dev instead of libglu-dev
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  libglu1-mesa-dev: Depends: libglu1-mesa (= 6.5.1~20060817-0ubuntu3) but 6.5.1+cvs20060824 is to be installed
                    Depends: libgl1-mesa-dev but it is not going to be installed or
                             libgl-dev
E: Broken packages
admin@KAYNOOK:~$ sudo apt-get install libglu-dev libsdl1.2-dev libglu1-mesa
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libglu1-mesa-dev instead of libglu-dev
libglu1-mesa is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  libglu1-mesa-dev: Depends: libglu1-mesa (= 6.5.1~20060817-0ubuntu3) but 6.5.1+cvs20060824 is to be installed
                    Depends: libgl1-mesa-dev but it is not going to be installed or
                             libgl-dev
E: Broken packages
admin@KAYNOOK:~$ sudo apt-get install libglu-dev libsdl1.2-dev libgl1-mesa-dev libgl1-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libglu1-mesa-dev instead of libglu-dev
E: Couldn't find package libgl1-dev
admin@KAYNOOK:~$ sudo apt-get install libglu-dev libsdl1.2-dev libgl1-mesa-dev libgl-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libglu1-mesa-dev instead of libglu-dev
Package libgl-dev is a virtual package provided by:
  libgl1-mesa-swx11-dev 6.5.1~20060817-0ubuntu3
  libgl1-mesa-dev 6.5.1~20060817-0ubuntu3
You should explicitly select one to install.
E: Package libgl-dev has no installation candidate
admin@KAYNOOK:~$ sudo apt-get install libglu-dev libsdl1.2-dev libgl1-mesa-dev libgl1-mesa-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libglu1-mesa-dev instead of libglu-dev
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  libgl1-mesa-dev: Depends: mesa-common-dev (= 6.5.1~20060817-0ubuntu3) but 6.5.1+cvs20060824 is to be installed
  libglu1-mesa-dev: Depends: libglu1-mesa (= 6.5.1~20060817-0ubuntu3) but 6.5.1+cvs20060824 is to be installed
E: Broken packages
admin@KAYNOOK:~$ sudo apt-get install libglu-dev libsdl1.2-dev libgl1-mesa-dev libgl1-mesa-dev mesa-common-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libglu1-mesa-dev instead of libglu-dev
mesa-common-dev is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  libgl1-mesa-dev: Depends: mesa-common-dev (= 6.5.1~20060817-0ubuntu3) but 6.5.1+cvs20060824 is to be installed
  libglu1-mesa-dev: Depends: libglu1-mesa (= 6.5.1~20060817-0ubuntu3) but 6.5.1+cvs20060824 is to be installed
E: Broken packages
admin@KAYNOOK:~$ sudo apt-get install libglu-dev libsdl1.2-dev libgl1-mesa-dev libgl1-mesa-dev mesa-common-dev libglu1-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libglu1-mesa-dev instead of libglu-dev
mesa-common-dev is already the newest version.
E: Couldn't find package libglu1-dev
admin@KAYNOOK:~$ sudo apt-get install libglu-dev libsdl1.2-dev libgl1-mesa-dev libgl1-mesa-dev mesa-common-dev libglu1-mesa
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libglu1-mesa-dev instead of libglu-dev
mesa-common-dev is already the newest version.
libglu1-mesa is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  libgl1-mesa-dev: Depends: mesa-common-dev (= 6.5.1~20060817-0ubuntu3) but 6.5.1+cvs20060824 is to be installed
  libglu1-mesa-dev: Depends: libglu1-mesa (= 6.5.1~20060817-0ubuntu3) but 6.5.1+cvs20060824 is to be installed
E: Broken packages


---

### Post by Mickeysofine1972 on 2006-11-27
Try using the package manager instead.

Mike

---

### Post by VDM on 2006-11-27
I have an issue on a box with libglu1-mesa stuff as well. Though i am not sure, i think it is because of 3th party compiz stuff.

Do you have any form of desktop bling installed?

---

### Post by kthakore on 2006-11-27
I do have beryl installed.

---

### Post by Mickeysofine1972 on 2006-11-27
I have beryl installed too but I'm not running it when I run my howtos

Although i don't think that makes a difference. just a though anyhoo

Mike

---

### Post by kthakore on 2006-11-28
What else can I do?

---

### Post by VDM on 2006-11-28
I think the issue is caused by an older compiz install or so.
I compiled SDL myself without OpenGL support. :(

---

### Post by Mickeysofine1972 on 2006-11-28
You could install beryl instead if you havent already .

I run beryl on my box and its fine.

Mike

---

### Post by kthakore on 2006-11-28
I already have beryl installed.

---

### Post by Mickeysofine1972 on 2006-11-28
Did you install ubuntu from the beta version of edgy or is it and upgrade through the web or even a upgrade from dapper?

I found that when the new version of edgy came out i had to wipe and reinstall as the updates broke my nvidia stuff.

So I'm running a almost fresh install of edgy from the RC version not beta or upgraded either.

Mike

---

### Post by kthakore on 2006-11-28
I upgraded from dapper

---

### Post by Mickeysofine1972 on 2006-11-29
You might consider backing up your data an doing a reinstall of edgy then.

I know the upgrade process is good but its not perfect.

Mike

---

### Post by hod139 on 2006-11-29
> **Mickeysofine1972 said:**
> 
If your doing OpenGL stuff you will also need:
freeglut3
freeglut3-dbg
freeglut3-dev

glut isn't needed to do OpenGL stuff with SDL.  You only have to install mesa-common-dev.  Most likely you will also want libglu1-mesa-dev as well (for the glu* functions).  Glut is a cross platform window kit, and depends on the two packages I just wrote.

---

### Post by Mickeysofine1972 on 2006-11-29
I will adjust the howto so that is more accurate but just so others don't panic, I will note that they will still be able to run and compile these howto anyway if they followed the older howto information

Mike

---

### Post by hod139 on 2006-11-29
> **Mickeysofine1972 said:**
> I will adjust the howto so that is more accurate but just so others don't panic, I will note that they will still be able to run and compile these howto anyway if they followed the older howto information

Mike
Good point.  OpenGL apps will still work if you install GLUT since glut depends on the OpenGL development libraries/headers. We just want to encourage the use of SDL in replace of GLUT.

---

### Post by Mickeysofine1972 on 2006-11-29
Well the story goes like this....

I was compiling a howto on setting up and someone asked howto setup opengl, (admittedly I have no clue!), so I began researching how to do it :-)

When compiling the lovely program from the SDL site it gave a compile error of can't find glu.h or something like that!

Sooo I figure i would install glut as I heard glut has something to do with glu ( mostly the 't' on the end apparently :-D) so installed those libraries and lo and behold! it worked!

so I figured I had done the right thing LOL!

Just shows you ... any idiot can program games !

Mike

PS - did I ever tell about the strange magnetic force that surrounds my body?

---

### Post by falkenberg_cph on 2006-12-01
Hi
Im getting an error when executing the compiled test program. Im not sure it has anything to with SDL. I tried reinstalling ALSA, but im getting the same problem. Anyone can tell whats up?

/Carsten

> 
carsten@carsten-laptop:~/Desktop/C++$ ./test-sdl
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix_format'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3957:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2143:(snd_pcm_open_noupdate) Unknown PCM dmix:SI7012
carsten@carsten-laptop:~/Desktop/C++$ 


---

### Post by Mickeysofine1972 on 2006-12-01
> **falkenberg_cph said:**
> Hi
Im getting an error when executing the compiled test program. Im not sure it has anything to with SDL. I tried reinstalling ALSA, but im getting the same problem. Anyone can tell whats up?

/Carsten

I did some sniffing around and it does indeed look like a problem with alsa. Although I can only advised a reinstall myself and you've done that.

However, please check the list of libraries to install in the HOWTO just to make sure you have them all.

Also if the problem continues you must bare in mind that we are testing these HOWTOs mostly on Edgy with a clean install of the latest RC. we cant cover problems with dapper or beta versions of Edgy as we don't have the resources atm.

Hope this helps

Mike

---

### Post by niiize on 2009-08-02
Thanx for sharing

---

### Post by greenmonkeey on 2011-04-24
is it worth to learn sdl for gaming programming?

---

