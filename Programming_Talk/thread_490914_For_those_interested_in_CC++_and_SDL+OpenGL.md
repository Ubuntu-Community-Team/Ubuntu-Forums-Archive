---
title: "For those interested in C/C++ and SDL+OpenGL"
date: 2007-07-03
forum: Programming Talk
---

### Post by slavik on 2007-07-03
attached is a simple game which I wrote for my game programming class a year ago ...

it includes some basic things, some more advanced things, and some interesting things :)

basic:
- uses OpenGL to draw stuff :P

advanced:
- complex and messed up keypress tracking system (never bothered to clean it up)
- a "timer" which will not let the game go voer 100fps, and will also move car at same speed even if the fps is 1 ...
- animated wheels :D (but I animate them in OpenGL, which is not very convenient)

interesting thigs:
- all models and textures are loaded from files, the model loading code was written by me from scratch by following the Wavefront OBJ spec.
- HUD :D, the game is 3D but the FPS counter is 2D overlayed :)

get it here:
[http://bcacm.org/~slavik/AI-Escape.tar.bz2](http://bcacm.org/~slavik/AI-Escape.tar.bz2)

---

### Post by nitro_n2o on 2007-07-03
downloading...  
That sounds interesting i wanted to start OpenGl programming and  i thinking looking at some working example is good..but is it documented?

---

### Post by Mickeysofine1972 on 2007-07-04
Hey Slavik

If you can write me a HOWTO based on your code I'd be happy to include it in the Ubuntu Games Developer Wiki ([http://ubuntu-gamedev.wikispaces.com](http://ubuntu-gamedev.wikispaces.com))

Mike

---

### Post by slavik on 2007-07-04
I hope you can understand the code (nothing cryptic in it I think, except for the timings stuff)

the only thing to watch out for is where I scan the keyboard (the logic of checking keys is messed up) and the transformation stuff (I think it has to be redone ...)

as for the howto, I will when I have time.

---

### Post by Mickeysofine1972 on 2007-07-05
> **slavik said:**
> I hope you can understand the code (nothing cryptic in it I think, except for the timings stuff)

the only thing to watch out for is where I scan the keyboard (the logic of checking keys is messed up) and the transformation stuff (I think it has to be redone ...)

as for the howto, I will when I have time.

Kewl

The more info we have the better it gets for all of us :D

Mike

---

### Post by waggygee on 2007-07-05
> **slavik said:**
> attached is a simple game which I wrote for my game programming class a year ago ...

it includes some basic things, some more advanced things, and some interesting things :)

basic:
- uses OpenGL to draw stuff :P

advanced:
- complex and messed up keypress tracking system (never bothered to clean it up)
- a "timer" which will not let the game go voer 100fps, and will also move car at same speed even if the fps is 1 ...
- animated wheels :D (but I animate them in OpenGL, which is not very convenient)

interesting thigs:
- all models and textures are loaded from files, the model loading code was written by me from scratch by following the Wavefront OBJ spec.
- HUD :D, the game is 3D but the FPS counter is 2D overlayed :)

get it here:
[http://bcacm.org/~slavik/AI-Escape.tar.bz2](http://bcacm.org/~slavik/AI-Escape.tar.bz2)

Im going to start studying Computer engineering in August and wanted to get a head start on programming Is this OK for a complete beginner at programming?

---

### Post by andyrobo60 on 2007-07-05
> **waggygee said:**
> Im going to start studying Computer engineering in August and wanted to get a head start on programming Is this OK for a complete beginner at programming?
If you are a beginner you should learn how to program normal C/C++ before you go onto learn things like OpenGL.

---

### Post by slavik on 2007-07-05
> **andyrobo60 said:**
> If you are a beginner you should learn how to program normal C/C++ before you go onto learn things like OpenGL.

QFT!

IMO, my code is good if you have some knowledge of C and want a 'working' example of how to make a simple OpenGL application.

---

### Post by moma on 2007-07-05
Excellent product Slavik. Your code is a very good example.

Though I had problems with compiling the Slavik's source so I re-packaged it slightly. I did not touch the code. (even Slavik has released it under GPL).

It requires at least these Ubuntu packages:
$ [COLOR="SeaGreen"]sudo apt-get install build-essential[/COLOR]
$ [COLOR="SeaGreen"]sudo apt-get install freeglut3-dev[/COLOR]
$ [COLOR="SeaGreen"]sudo apt-get install  libsdl1.2-dev  libsdl-mixer1.2-dev  libsdl-image1.2-dev libsdl-sound1.2-dev[/COLOR]

+ Mesa opengl support.

( maybe the libsdl-sound1.2-dev is not required, anyway..)

Download the enclosed tar.gz ball.

0) Untar it.

1) cd into the slavik_game directory. Configure and compile (make) the source.
$ cd slavik_game
$ ./configure 
$ make clean 
$ make 

2) Run it  (the executable name is ./main in src directory)
$ cd src 
$ ./main 

Note: You can learn more about the package by studying
"Makefile.am", "src/Makefile.am", "configure.in" and "autogen.sh" files.

Google for guides about "automake autoconf"

Or read [this..]("http://sources.redhat.com/automake/automake.html") manual.  Browse down to "Hello World" example. 
or take a look at [this..]("http://www.seul.org/docs/autotut/").

Someone should tell me what is the correct way to set the LDFLAGS variable in configure.in or Makefile.am .  I tried many ways..

Source package:  [http://www.futuredesktop.org/tmp/slavik_game.tar.gz](http://www.futuredesktop.org/tmp/slavik_game.tar.gz)

---

### Post by slavik on 2007-07-05
yeah, I did not package it, just realeased my anjuta project directory :P

SDL_Sound is not required (there is no sound at all)

---

### Post by Druke on 2007-07-14
link broken?

---

### Post by moma on 2007-07-14
See my previous posting.

---

### Post by slavik on 2007-07-14
> **Druke said:**
> link broken?
seems like the server went down again ... give it like 5-10 min and try again, I will (meanwhile) post the file elsewhere.

---

### Post by djhworld on 2007-07-14
Heh that's pretty cool!

Question: What are you supposed to do exactly? (within the game)

---

### Post by Wybiral on 2007-07-14
Neat, though I can't help but notice the mixture between SDL and glut. I would suggest using SDL_tff to render the text on the screen. But, aside from that, and some areas of potential code-reuse, it looks pretty nice.

If you even plan on extending it or starting a small project from (or similar) to that, I would be glad to pitch in on some areas (I'm pretty well versed with OpenGL and both C and C++).

---

### Post by slavik on 2007-07-14
I didn't want to bother with SDL_ttf because I think it created a new SDL_Surface anytime it renders anything, I have an idea of using SDL_ttf to pre-render a font and then use textured quads to put messages together.

for tha game, there is no way to "win" (there is no collision detection nor is there any winning scenario)

---

### Post by Wybiral on 2007-07-14
> **slavik said:**
> I didn't want to bother with SDL_ttf because I think it created a new SDL_Surface anytime it renders anything, I have an idea of using SDL_ttf to pre-render a font and then use textured quads to put messages together.

That makes sense... I haven't gotten around to test SDL_ttf for performance, but if it's not too slow, it could easily be wrapped in a function so you didn't have to deal with the new SDL_Surface mid-code.

The pre-render might work, I've seen people use a grid of a font in an image and then use quads and adjusted texture coords to render text in OpenGL.

Any plans on making a functional game from this?

---

### Post by gvoima on 2007-07-14
Hehe, a nice one :)

I was planning on some OpenGL programming, fed up with my current projects anyway :(

---

### Post by slavik on 2007-07-14
> **Wybiral said:**
> That makes sense... I haven't gotten around to test SDL_ttf for performance, but if it's not too slow, it could easily be wrapped in a function so you didn't have to deal with the new SDL_Surface mid-code.

The pre-render might work, I've seen people use a grid of a font in an image and then use quads and adjusted texture coords to render text in OpenGL.

Any plans on making a functional game from this?

that is how HL and mods do it, not sure about HL2 ...

also, the reason for using prerendered textures and textured quads is to use only opengl for drawing and thus speeding it up (in case sdl_ttf doesn't use opengl)

I wanted to, but dunno if I will now ...

---

### Post by Wybiral on 2007-07-14
> **slavik said:**
> I wanted to, but dunno if I will now ...

Why is that?

---

### Post by AlexThomson_NZ on 2007-07-14
I render text using GL Quads, rathen than with SDL (which seems to be broken anyway- ie. rendering spaces with *_solid).  I have some code if anyones interested.

Anyway, nice little demo you got there.  I'm finishing up something myself (an old-skool demo type  program just to show off my l33t GL skillz ;) ) I'll put it up when I'm done...

---

### Post by slavik on 2007-07-14
> **Wybiral said:**
> Why is that?
time ... there are other things I want to work on

- dcc chat for pidgin
- a skeleton c/cpp/python/perl generator given a glade file (seems like perl doesn't have a module that supports glade3 xml ...

---

