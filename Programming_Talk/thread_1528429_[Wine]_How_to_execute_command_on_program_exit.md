---
title: "[Wine] How to execute command on program exit?"
date: 2010-07-10
forum: Programming Talk
---

### Post by asorron on 2010-07-10
well title says it all...
Iv'e set Wine to cause a change of my resolution (I.E running PES2010 under 1024x768, im running at 1280x800)
What i want to do is to peform xrandr -s 1280x800 on wine (or more likely PES2010.exe) exit. how do i pull it off?

Thanks

---

### Post by lisati on 2010-07-10
Options that come to mind include setting up a shell script or (.bat file for Wine) as a wrapper for your program that runs a program after the main program.

If it's a program you've written yourself, you might want to check out the [atexit()]("http://www.cplusplus.com/reference/clibrary/cstdlib/atexit/") function in C/C++

---

### Post by phrostbyte on 2010-07-10
A shell script with something like this should do it.

#! /bin/sh
wine blahblah.exe
xrandr -s 1280x800

---

### Post by asorron on 2010-07-11
> **phrostbyte said:**
> A shell script with something like this should do it.

#! /bin/sh
wine blahblah.exe
xrandr -s 1280x800

will it cause the command to execute on exit? or after wine is loaded? since i need it after wineserver closed down...

P.S;
just noticed, dont you mean

##!bin/bash

---

### Post by asorron on 2010-07-11
For some reason it isnt working at it should be...
It says it's not installed correctly
I think I need to launch it within the game's environment  (it says the game isnt installed or such, but navigating manually on terminal to the game's folder works. but the difference is when I launch the game itself it will pull it to fullscreen, and by command line it stays on window mode)
I still dont have much to figure what to do... since i'm kinda new at this but I'm always trying to learn further.

Any help will be welcomed.

Thanks

---

### Post by asorron on 2010-07-11
Okay got it. I had an exception to run the game (executable file) with resolution of 1024x768 which is bad, it needed to set to run without a virtual desktop (so it set it to fullscreen that way) and after the client exit it returned the regular resolution.

now only one thing left, adding it to the applications > games tab. i think i know how to do that O.o'...

```
##!/bin/bash
cd /home/ron/&#1513;&#1493;&#1500;&#1495;&#1503;\ &#1506;&#1489;&#1493;&#1491;&#1492;/Pro\ Evolution\ Soccer\ 2010
wine pes2010.exe
xrandr -s 1280x800

```
thats the  main way i got it, i tried to run it by inputting the whole path of it, as ```
wine '/home/usr/......' 
```
which didnt worked out...
the above worked as the latter said game isnt installed.
maybe ill even add it to /usr/bin/ folder for easy terminal access :]

---

### Post by phrostbyte on 2010-07-11
It's really just #!

[http://en.wikipedia.org/wiki/Hashbang](http://en.wikipedia.org/wiki/Hashbang)

#!/bin/sh

tells the shell to execute the script with the system shell. /bin/bash also works too, but your script would be slightly slower executing on bash instead of the system shell.

[PHP][ ~ ] echo "echo Blah blah blady blah.." > test.sh
[ ~ ] time sh test.sh
Blah blah blady blah..

real	0m0.004s
user	0m0.004s
sys	0m0.000s
[ ~ ] time bash test.sh
Blah blah blady blah..

real	0m0.013s
user	0m0.008s
sys	0m0.004s
[/PHP]

---

