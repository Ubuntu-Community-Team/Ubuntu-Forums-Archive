---
title: "New Howto on Ubuntu Games Developer Resource Wiki!"
date: 2006-12-07
forum: Programming Talk
---

### Post by Mickeysofine1972 on 2006-12-07
here the link:
[http://ubuntu-gamedev.wikispaces.com/](http://ubuntu-gamedev.wikispaces.com/)

Mike

---

### Post by hod139 on 2006-12-07
I got an error when trying to build this demo, it looks like there is a typo in your makefile.  Instead of just negative feedback, I wrote a fix :).  Here is a (slightly different) makefile that works

```

CC=g++

SDL_CFLAGS := $(shell sdl-config --cflags)
SDL_LDFLAGS := $(shell sdl-config --libs) -lSDL -lSDL_image

#CFLAGS = -g  #Debug
CFLAGS = -O2  #release
CFLAGS +=  ${SDL_CFLAGS}


LIBS=  ${SDL_LDFLAGS} 

test:         platform.cpp support.a
        $(CC) $(CFLAGS) -c platform.cpp
        $(CC) platform.o support.a $(LIBS) -o test

support.a:    tilelayer.cpp font.cpp
        $(CC) $(CFLAGS) -c tilelayer.cpp font.cpp
        ar rsc support.a tilelayer.o font.o
        ranlib support.a

clean:
        rm -f support.a *.o

```Changes:
Fixed spelling of libs
Separated out the SDL cflags and libs into their own variables
added the -O2 flag (turns on level 2 optimizations)
added -f flag to rm (removes annoying nag messages in case the files to delete do not exists)
added support.a to clean rule

Cool tutorial btw.

---

### Post by po0f on 2006-12-07
Mickeysofine1972,

I have been noticing that you are posting a lot of HOW-TOs here in PT.  I haven't browsed all the threads but I am sure that they contain a lot of useful information.  At some point in the future (anytime between now and never) I plan on programming a game.  Thank you for figuring it out for the rest of us and putting it all together on a wiki.  :)

---

### Post by sailingboarder on 2006-12-07
looks like a very good resource
when i have more time(i.e. tomorrow):)  i plan on going back and thoroughly investigate it
thankyou Mickeysofine1972 for making those resources avaliable to everyone

---

### Post by Mickeysofine1972 on 2006-12-08
> **hod139 said:**
> I got an error when trying to build this demo, it looks like there is a typo in your makefile.  Instead of just negative feedback, I wrote a fix :).  Here is a (slightly different) makefile that works

```

CC=g++

SDL_CFLAGS := $(shell sdl-config --cflags)
SDL_LDFLAGS := $(shell sdl-config --libs) -lSDL -lSDL_image

#CFLAGS = -g  #Debug
CFLAGS = -O2  #release
CFLAGS +=  ${SDL_CFLAGS}


LIBS=  ${SDL_LDFLAGS} 

test:         platform.cpp support.a
        $(CC) $(CFLAGS) -c platform.cpp
        $(CC) platform.o support.a $(LIBS) -o test

support.a:    tilelayer.cpp font.cpp
        $(CC) $(CFLAGS) -c tilelayer.cpp font.cpp
        ar rsc support.a tilelayer.o font.o
        ranlib support.a

clean:
        rm -f support.a *.o

```Changes:
Fixed spelling of libs
Separated out the SDL cflags and libs into their own variables
added the -O2 flag (turns on level 2 optimizations)
added -f flag to rm (removes annoying nag messages in case the files to delete do not exists)
added support.a to clean rule

Cool tutorial btw.

Hi Hod139

That you for your positiveness! I have identified the offending line: 
```

LIBS=`sdl-config --cflags --lins` -lSDL -lSDL_image

```

it should read :
```

LIBS=`sdl-config --cflags --libs` -lSDL -lSDL_image

```

I guess thats what you call a fruedian slip! LOL

I'll redo the zip and replace ASAP :-D

Mike

---

### Post by Mickeysofine1972 on 2006-12-08
> **sailingboarder said:**
> looks like a very good resource
when i have more time(i.e. tomorrow):)  i plan on going back and thoroughly investigate it
thankyou Mickeysofine1972 for making those resources avaliable to everyone

Thanks sailingboarder & Po0f We appreciate the encouragement! but bare in mind that the credit goes to the whole team:

VDM
WyBiral
Choad

Great works lads!

BTW VDM is working on a Makefile HOWTO as of yesterday and we will be interested to see how we can incorporate that into our projects too! :-D 

Mike

---

### Post by Mickeysofine1972 on 2006-12-08
coz its the weekend BUMP!

---

### Post by po0f on 2006-12-08
Mickeysofine1972,

Let me know when the make tutorial gets put up, I might be able to contribute to that one.  Then again, I may learn a thing or two instead.  ;)

---

### Post by Mickeysofine1972 on 2006-12-09
Actually if you would like to contribute VDM is currently writting it on the wiki so if you would like access to contribute please email me a contact email and I will send you an invite.

my email is [email]hibbert_michael@hotmail.com[/email]

Mike

---

### Post by Turk on 2006-12-09
Thanks, great tutorials.

---

### Post by Mickeysofine1972 on 2006-12-09
we aim to please ! ;-)

More coming soon!

I'm currently working on a Sprite Class that will interact with other sprites and the tiled layers in my last HOWTO so watch this space!

Mike

---

