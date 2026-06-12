---
title: "C++ and Graphics"
date: 2008-07-20
forum: Programming Talk
---

### Post by loganwm on 2008-07-20
I've been using Ubuntu and Kubuntu almost exclusively for the last few months and I've begun studying C++ programming and techniques, and I figured I'd try asking the community for a few pointers.

I'm familiar with programming fundamentals and I've already learned quite a bit of Lua scripting on another platform (lua.org) and a small amount of Visual Basic, but I'm interested in C++ programming.

I've gone through some tutorials on C++ standard functions and SDL but I'm not sure where to go about some of the following topics

[LIST]
[*]Use of graphics and drawing functions
[*]Obtaining keyboard input and mouse input
[/LIST]

I'm very grateful for any assistance and I'm hoping I can get involved in this community.

---

### Post by mike_g on 2008-07-20
It might be worth sticking with SDL for a bit. THeres some good computer graphics tutorials on this site:

[http://student.kuleuven.be/~m0216922/CG/](http://student.kuleuven.be/~m0216922/CG/)

For for input you would generally set your program to run in a loop and poll for events reguarly. Examples in SDL:

[http://lazyfoo.net/SDL_tutorials/lesson08/index.php](http://lazyfoo.net/SDL_tutorials/lesson08/index.php)
[http://lazyfoo.net/SDL_tutorials/lesson09/index.php](http://lazyfoo.net/SDL_tutorials/lesson09/index.php)

---

### Post by loganwm on 2008-07-20
SDL is one option that I have been looking at, but are there any alternative libraries for similiar functions? (Keeping my options open, rather than narrow my view of the matter)

Another thing that I have interest in is the windowing system. On my other platforms I haven't ever had to create or initialize window objects, will the SDL/alternative libraries do this for me (with a bit of guidance) or is another library needed (GTK/KDE/etc.)?

And Kudos on the quick reply.

Edit:
And I've gone into Synaptic and installed the SDL development and runtime files, anything else necessary in the setup?

---

### Post by loganwm on 2008-07-20
I don't mean to "bump" my own post, but I have another question I'm hoping to get help with.

With the SDL demo's I've downloaded there's a makefile included, and I understand that they're used with the 'make' command, but how is it that a makefile is generated and what do I need to know to move forward?

---

### Post by slavik on 2008-07-21
a makefile can be written by hand or generated using autoconf ...

don't worry about generating a makefile (write one by hand for now).

---

### Post by Sockerdrickan on 2008-07-21
> **loganwm said:**
> I've been using Ubuntu and Kubuntu almost exclusively for the last few months and I've begun studying C++ programming and techniques, and I figured I'd try asking the community for a few pointers.
0xbf7ff4c4
0xbf803718
0xbf83b1d4
0xbf8e24d4
0xbfaf4c0c

---

### Post by nvteighen on 2008-07-21
> **Tux0r said:**
> 0xbf7ff4c4
0xbf803718
0xbf83b1d4
0xbf8e24d4
0xbfaf4c0c
Segmentation fault (core dump)

---

### Post by mike_g on 2008-07-21
> Another thing that I have interest in is the windowing system. On my other platforms I haven't ever had to create or initialize window objects, will the SDL/alternative libraries do this for me (with a bit of guidance) or is another library needed (GTK/KDE/etc.)?
SDL will setup a window to run your prog in if you leave omit the SDL_FULLSCREEN flag when you call SDL_SetVideoMode to set up the screen buffer. If you want multiple windows with gui widgets you might want to consider a lib such as GTK+, but GTK is a bit more complex to work with. Personally I'd stick with SDL for a bit.

Like slavik said you shouldent need to worry about makefiles for now. You can compile a simple SDL app in one source file by simply typing:
```
g++ sourcefilename.cpp -Wall -lSDL
```
When your project starts getting more complex google for a compiling with g++ tutorial.

---

### Post by loganwm on 2008-07-21
I'm actually amazed at how quick the replies came in.

On the g++ line, the '-lSDL' is something that's been bugging me, on other SDL apps that I tried to make (learning by doing.. haha) they wouldn't compile and said that they had undefined references, so I'm assuming that this fixes that. Do most referenced libraries need a flag like this for the compiler?

I've also seen it in the Makefiles I've dissected (I'm not a complete noob :) )

---

### Post by LaRoza on 2008-07-21
> **loganwm said:**
> I'm actually amazed at how quick the replies came in.

Sorry, we'll slow them down for you :-)

> 
On the g++ line, the '-lSDL' is something that's been bugging me, on other SDL apps that I tried to make (learning by doing.. haha) they wouldn't compile and said that they had undefined references, so I'm assuming that this fixes that. Do most referenced libraries need a flag like this for the compiler?
It links the libraries. For the standard libs, it isn't needed (except for math, -lm)

---

### Post by WW on 2008-07-21
> **loganwm said:**
> 
On the g++ line, the '-lSDL' is something that's been bugging me, on other SDL apps that I tried to make (learning by doing.. haha) they wouldn't compile and said that they had undefined references, so I'm assuming that this fixes that.

It should.  This tells the linker that your program will use the SDL library.

By the way, in [this list of files](http://packages.ubuntu.com/hardy/i386/libsdl1.2-dev/filelist), you can see that the libsdl.2-dev package includes the file /usr/lib/pkgconfig/sdl.pc.  This is a configuration file for the **pkg-config** command.  You can use this to get all the compiler and linker options required for the library.  For example,
```

$ pkg-config --cflags sdl

```
shows the required compiler options, and
```

$ pkg-config --libs sdl

```
shows the required linker options. You can give both options --cflags and --libs to the command, and you can put the command in back-ticks and use it as part of your g++ command, like this:
```

g++ sourcefilename.cpp -Wall `pkg-config --cflags --libs sdl`

```
I don't have the library installed, so I don't know what pkg-config says about sdl.  It may be that -lSDL is the only option needed, so the pkg-config command doesn't help much.  Some other libraries require more complicated arguments, so pkg-config can make life much easier.
> **loganwm said:**
> 
 Do most referenced libraries need a flag like this for the compiler?

Yes (but not all libraries provide a configuration file to be used with pkg-config).

---

### Post by loganwm on 2008-07-21
If I need a flag like this for a library, is there anywhere special I need to look or will the programming fairy leave it under my pillow?

---

### Post by mike_g on 2008-07-21
> On the g++ line, the '-lSDL' is something that's been bugging me, on other SDL apps that I tried to make (learning by doing.. haha) they wouldn't compile and said that they had undefined references, so I'm assuming that this fixes that.
It could have been that the progs you tried to compile were using some of the extra SDL libs, such as: SDL_mixer, SDL_ttf or SDL_gfx. in which case I think you would need to link them too.

---

### Post by loganwm on 2008-07-21
> **mike_g said:**
> It could have been that the progs you tried to compile were using some of the extra SDL libs, such as: SDL_mixer, SDL_ttf or SDL_gfx. in which case I think you would need to link them too.

Using -lSDL wouldn't cover the other SDL libs as well?

Or am I not following correctly?

---

### Post by nvteighen on 2008-07-21
> **loganwm said:**
> Using -lSDL wouldn't cover the other SDL libs as well?

Or am I not following correctly?
No. -l*xxx* will look for a file called lib*xxx*.so in the library folders (by default: /lib, /usr/lib, /usr/local/lib).

To get all libraries related to a package, use WW's advice.

---

### Post by loganwm on 2008-07-21
> **nvteighen said:**
> No. -l*xxx* will look for a file called lib*xxx*.so in the library folders (by default: /lib, /usr/lib, /usr/local/lib).

To get all libraries related to a package, use WW's advice.

I actually found the answer to my own question about 2 seconds before you posted, but I'm grateful anyway. :)

---

### Post by Lster on 2008-07-21
I would recommend OpenGL as another great graphics library. You can use SDL to setup everything for OpenGL, and then OpenGL for the rendering. It's easy, fast and has great documentation and tutorials.

---

### Post by loganwm on 2008-07-21
For a tile-based engine, would SDL suffice?

And I've got a couple more questions as I'm moving forward:
[LIST]
[*]Rotating images with SDL
[*]Does SDL have native drawing functions?
[/LIST]

---

### Post by Sockerdrickan on 2008-07-21
My cpu runs at 1-7% with my FreePokemon game and that's very high on a AMD 6400+
So yeah SDL's render calls are pretty inensive even though you convert images to the right depth and don't use alpha channels on pics that doesn't need em.

---

### Post by loganwm on 2008-07-21
> **Tux0r said:**
> My cpu runs at 1-7% with my FreePokemon game and that's very high on a AMD 6400+
So yeah SDL's render calls are pretty inensive even though you convert images to the right depth and don't use alpha channels on pics that doesn't need em.

How big of a chunk of your map is rendered at any given time?

I've seen the demo video you posted, but I'm not really sure as to how efficiently its dealing with the SDL rendering, I'm just trying to guage the SDL library in general.

---

### Post by Sockerdrickan on 2008-07-22
As I said, I have taken actions but it's still using a lot of CPU... the window is 160x144 in my videos

edit
[img]http://img33.picoodle.com/img/img33/4/7/21/f_SkrmbildPokm_600ea83.png[/img]

---

### Post by Lster on 2008-07-22
With OpenGL, I can render each frame from scratch every 10 milliseconds and still use <1% of my Intel Core 2 T7300 CPU. It is exceptionally fast! ;)

Cool looking game, by the way. :)

---

### Post by nvteighen on 2008-07-22
I hope you'll reimplement the Missingno bug :)

---

### Post by mike_g on 2008-07-22
If youre playing a game does it relly make a difference whether it it uses 1% or %50 of the cpu time? as long as the game runs at a steady fps thats all that really matters. As with OpenGL thats just passing more instructions to the GPU. You can get a lot nicer effects using shaders and stuff, but IMO SDL would be better for a beginner.

---

### Post by Zugzwang on 2008-07-22
Note that the actual system load heavily depends on the implementation of the library. It might be the case that in Linux, SDL doesn't take advantage of 2D rendering acceleration of the graphic card (or the driver doesn't support that). Using Windows, SDL is normally not noticeably slower (if not faster).

---

### Post by loganwm on 2008-07-22
For use of particles and particle physics, which libraries are best? And for those mentioned libraries, are there any good particle physics demonstrations?

And again, I'm stunned by all of the responses.

---

