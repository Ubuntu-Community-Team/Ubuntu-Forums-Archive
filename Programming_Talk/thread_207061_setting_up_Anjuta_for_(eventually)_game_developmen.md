---
title: "setting up Anjuta for (eventually) game development"
date: 2006-07-01
forum: Programming Talk
---

### Post by blastradius on 2006-07-01
I've decided to have a real go at developing with C++, I'm ok at the basic stuff, I know my if...else and my do......while e.t.c. My plan is to do a complete clean install of Dapper (as my system has been filled with junk) get serious and hopefully get to a stage where I can start to think of graphics API's and all the extra bits that I would need to get some sort of game project going.

I'm a devoted Gnome user and would prefer to use Anjuta, my aim is to set up Anjuta with everything Installed that I would need in future, (when I've tried running example code like SDL or OpenGL stuff, there's always libs e.t.c. that aren't there).

What will I need to install along with Anjuta itself that will ensure that any code I may write in future will have all it needs already installed?  Can this be done from the Ubuntu repositories or will I need to download and install stuff manually? and how do I get Anjuta to 'see' these libs when they are installed? (I did download SDL and install it but couldn't get Anjuta to run with it).

As I said I'm a Gnome user but is there a better C/C++  IDE out there, I looked at Kdevelop but it seems way too complicated for my current needs and seems to push a user towards QT and KDE development.  It looks like it's built for seriously big developments rather than the kind of thing I'll be having a go at.  I've considered just using a text editor and compiling on command line but again how would I incorporate all the extra bits needed, If I write something in Gedit and it uses SDL, how do I compile it?

I think I've got a bit long winded about this but hopefully someone can make sense of this.

Thanks in advance 

Eric

---

### Post by gord on 2006-07-01
all you need to do to get librarys to work with the code you create with anjuta is download the <library>-dev files from the ubuntu repositorys (for example sdl-dev) then add the library to the librarys tab in the "compiler and linker settings". for example add 'SDL' to get access to the sdl librarys. 

then to get sdl working in your code you add
#include <SDL/SDL.h>

or you can add /usr/include/SDL to your include path and include sdl the prefered way
#include <SDL.h>


anjuta is fine for developing applications. right now i'm working on gens which is a megadrive emulator with anjuta. i'd suggest you stop looking for what you think you need and just use whatever your most comfortable in.

---

