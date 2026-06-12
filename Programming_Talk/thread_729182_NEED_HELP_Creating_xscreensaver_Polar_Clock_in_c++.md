---
title: "NEED HELP: Creating xscreensaver Polar Clock in c++/sdl/gl"
date: 2008-03-19
forum: Programming Talk
---

### Post by kthakore on 2008-03-19
I am trying to make a port of [http://blog.pixelbreaker.com/polarclock/]("http://blog.pixelbreaker.com/polarclock/") for the xscreensaver in ubuntu. Although this is my first SDL/GL application I have been able to get it running. However I am stuck at a few things

TODO:

- Found some stupid mem leaks with valgrind but can't seem to get rid of them
- the MainView class is too messy!!!
- Anti alias the rings
- Smoother animation
- Draw the texts in a circle at the end of each ring
- and the major one making it work with xscreensaver and gnome-screensaver.

Here is the source with both debug an release mode.

[http://kthakore.homelinux.com/PolarClock/PolarClock.tar.gz]("http://kthakore.homelinux.com/PolarClock/PolarClock.tar.gz")

 I used eclipse but u can still build them with make. You need SDL SDL ttf and GL libraries. 

Here is what it looks like now:

[IMG]http://kthakore.homelinux.com/PolarClock/polar.png[/IMG]



Any help is appreciated. Also can u please post you solutions here so I can learn too!!!

---

### Post by andrewkk on 2008-08-08
I'm excited for this. Though sadly I know nothing about graphics or memory management. :(

It seems like a simple enough project that I bet that all you'd need to to is hype it up a little more and someone out there would be able to throw something together in no time.

Perhaps the pixelbreaker blog owner would be willing to put up a message asking for interested coders to port PolarClock?

---

### Post by lunarcloud on 2008-09-11
where do i put it to make it a screensaver?

---

### Post by rnodal on 2008-09-12
> 
- Found some stupid mem leaks with valgrind but can't seem to get rid of them


Are you sure those memory leaks come from your application? Sometimes the memory leaks come from the library being used. Also do you have any code after SDL_Quit()? SDL_Quit calls exit and not return() so any code after SDL_Quit will not get executed so any destructor or memory freeing code will not get executed.

> 
- the MainView class is too messy!!!


Finish the application THEN clean the code. 

> 
- Anti alias the rings


Look into enabling multi-sampling with SDL. Or you can try OpenGL smooth curves, lines. I'm at work right now so I can't help much now on this. 

> 
- Smoother animation


Are you taking into account the delta time between frames? How are you doing your animation?

> 
- Draw the texts in a circle at the end of each ring


I have not really given any thoughts to the problem so I can't offer any solutions.

> 
- and the major one making it work with xscreensaver and gnome-screensaver.


The site of each project should offer information on this.

Other than that congratulations and keep up the good work!

-r

---

### Post by nulall on 2008-09-13
this looks awesome! i can't wait to see it. please give us an update of how it's coming along

---

### Post by Hasteur on 2009-03-03
Any chance that someone has the original source of this?  I'd be extremeley interested in reviving/supporting this if anybody had the source.

---

### Post by Delever on 2009-03-03
> **kthakore said:**
> 
- Draw the texts in a circle at the end of each ring


I recently made my text drawing code available here: [http://code.google.com/p/glstext/](http://code.google.com/p/glstext/)

Just a warning, right now it compiles and installs both library AND example (i need to change that), so use
```
./configure --prefix ~/test
make
make install
./bin/testglst
```
to check out example. Or don't run 'make install'. Anyway, you will need "FreeSerif.ttf" font to be in 'bin' for example to work.

You can create class similar to GLST_Text (it is simple), and change render method to draw text in a way you need (each symbol is simply textured quad).

EDIT: I think you can drop those glstext classes in eclipse and it will work, no need for "library".

---

### Post by Delever on 2009-03-03
Sorry, I haven't looked at the date of original post!

---

### Post by rugbert on 2009-03-10
bump! any update on this? i love this screesaver!

---

### Post by smCw6GNakQn300£ on 2009-03-25
> **rugbert said:**
> bump! any update on this? i love this screesaver!

ditto!

---

### Post by travnewmatic on 2009-05-12
bumpity bump, make it happen

---

### Post by Psyphre on 2009-06-21
bumpity bompity boop.

me too!

---

### Post by hackerseraph on 2010-06-28
Shameless BUMP

---

### Post by danger89 on 2010-08-06
So does it work?

---

### Post by UnicornForest on 2010-10-19
[LEFT][SIZE=3]** zibbidy bob hibbidy hop shim sham allakhazam!**[/SIZE]
And another spell from the great wizard of unicorn forest is made.   
[/LEFT]

[IMG]http://www.unicornforeststudios.com/spells/rainbow.jpg[/IMG]

Sorry guys I was trying to make a clone of that thing you wanted but looks like I just turned it into a rainbow.  This spell was written in C and uses SDL for windowing and Cario for rendering. It should be enough of a seed that one of the other technomancers around here should be able to grow it into that thing you guys were wanting.

Here is a link to a video:
[http://www.youtube.com/watch?v=lhTp-aBR2cU](http://www.youtube.com/watch?v=lhTp-aBR2cU)

And a link to the source:
[http://www.unicornforeststudios.com/spells/rainbowclock.tar.gz](http://www.unicornforeststudios.com/spells/rainbowclock.tar.gz)
(just untar and make)

---

### Post by Brejcha on 2011-01-10
Any more news on this. Anyone have a full linux conversion?

---

