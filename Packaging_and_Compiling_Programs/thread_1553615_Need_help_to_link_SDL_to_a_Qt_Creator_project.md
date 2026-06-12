---
title: "Need help to link SDL to a Qt Creator project"
date: 2010-08-15
forum: Packaging and Compiling Programs
---

### Post by DarkAmbient on 2010-08-15
When i try to build this SDL/C++ project I get undefined reference to all the SDL functions in the project. 

Normally I'm pretty sure you just add -lSDL as a parameter to g++?

But in this case I have no clue where to tell the compiler to include the SDL libs. 

Searched alot on this and cant rly find any good answer (using Qt creator).

I've played around alittle with the build steps. But changed them back to default as I did'nt make any progress.

Build step:
```
qmake-qt4 /home/myname/Project-Pagan/Project-Pagan.pro -spec linux-g++ -r
```

not sure if i should change anything there? Tried to add -lSDL to the end at that command, but it gave an error.

Also tried to add this to my .pro file.

```
INCLUDEPATH += /usr/include
QMAKE_CFLAGS += $$system(sdl-config --cflags)
QMAKE_CXXFLAGS += $$system(sdl-config --cflags)
```

as I found out that SDL is located  in /usr/include... and maybe it the dir was'nt included propertly. This did'nt make a difference though.

While at this.. I got this is my main.cpp and it worked well in bloodshed under windows. 

```
/* Linking the SDL library */
#pragma comment(lib, "sdl.lib")
#pragma comment(lib, "sdlmain.lib")
#pragma comment(lib, "sdlgfx.lib")
#pragma comment(lib, "sdl_mixer.lib")
```

But the compiler tells me it's ignoring it. Not sure if this information is usefull.

So anyway, I have no clue how to remove the undefined rerences to SDL. So please, help is appreciated.

PS. I'm rather sure i have all the sdl libs thats needed. Followed some guide on which one to pick via synaptic.

---

### Post by DarkAmbient on 2010-08-15
sorry for the doublepost. Found a workaround so help is'nt needed. 

Seems that im not able to delete this myself so im asking for this thread to be deleted please.

Thanks.

---

### Post by ShapeShiftme on 2010-12-18
Could you please explain the workaround or the link to where you found it as i am having the same problem

---

### Post by DarkAmbient on 2010-12-18
> **ShapeShiftme said:**
> Could you please explain the workaround or the link to where you found it as i am having the same problem

Hey, sure. But sorry to disappoint you. My "workaround" was that i switched ide to code::blocks for linking the sdl libs. Still no idea how to link sdl libs (if possible) in qtcreator.

Hope you find a solution though. Cheers

---

### Post by mipesom on 2011-03-19
Just add something like this at the end of your .pro file:

```
LIBS += -L/usr/lib -lSDL -lSDL_image -lSDL_ttf

INCLUDEPATH = usr/include
```

Your path may be different and you've to adjust the example to the libs you actually want to use of course. ;)

---

### Post by Leo_san on 2011-03-21
It is not working here...
it is working on codeblocks and i just added the library SDL_net and included the path /usr/include/SDL

LIBS += -L/usr/lib -lSDL -lSDL_net
INCLUDEPATH += usr/include/SDL
INCLUDEPATH += usr/include

i tryied here to write this 3 lines in a dfferent order and still not compiling...
i dont know what to do :confused:

EDIT:
I forgot the "/" right after each INCLUDEPATH....
sorry =/

---

### Post by shbk on 2012-03-19
add only this one line to .pro : LIBS += -lSDL
 it looks like:
[http://www.imagepost.ru/?v=it_looks_like.png](http://www.imagepost.ru/?v=it_looks_like.png)

also you shall compile library(I build it from source code). I moved   headers include folder  explicitly to /usr/inlcude

---

