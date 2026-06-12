---
title: "Mute! A wonder-where-to-start question"
date: 2008-02-07
forum: Programming Talk
---

### Post by wrightee on 2008-02-07
I'm pondering a little project and wondering where other programmers might begin...  

We've got a shiny linux box sitting in the corner of our little office which runs a mix of various OSs.  I have this nagging idea that I want it to play music, but to do that practically anyone needs to be able to mute it when the phone rings or other such interruptions occur.

Remote access is overkill, and not practical.  A big red mechanical switch on everyone's desks sounds fun, but beyond my wiring skills..  

So I'm guessing some kind of script to listen on a particular port for a simple instruction to mute / unmute would be the interesting-coding way to go...

I was wondering how anyone else might tackle the problem (and secretly hoping to read something like 'just sudo apt-get install mute-me-over-the-network'. Ho ho.

All the best!

---

### Post by CptPicard on 2008-02-07
Amarok and DCOP. Either write a little script that does what you describe and calls the DCOP interface... or, I'm not sure of this, maybe DCOP can be used over the network as it is.

---

### Post by xlinuks on 2008-02-07
Have you actually tried to use the command you mentioned? It might work :)
On the other hand, the player you're using might be listening to a port on your computer for different commands, so you might just create a shell script or alike to tell it what you need.

---

### Post by lnostdal on 2008-02-07
add the rsa key of each of the office machines to the authorized keys of the "music box" .. you can now use ssh(#1) to execute the amixer command remotely and directly on the "music box" from the office machines .. :)

* see *man 1 amixer*
* see [http://www.openssh.com/windows.html](http://www.openssh.com/windows.html) if your office computers are running windows

#1: without having to enter a username/password ofc. .. it's instantaneously and direct .. i'm not talking about logging in remotely and *then* executing a command in a terminal window .. this will execute the amixer command directly (you supply the arguments that mute or de-mute ofc.) without opening a window/terminal of any sort .. point is to make it transparent

---

### Post by ruy_lopez on 2008-02-07
You can try ssh and alsa-mixer. Log into to the music player. Bring up alsa mixer. Move the cursor to the master volume. Use the 'M' key to mute.

EDIT: Same as above, I see. Except I'd keep alsa-mixer up and ready, waiting till the phone rings. Then just press M.

```
sudo apt-get install alsa-utils
```

Installs the ncurses version of alsamixer.

---

### Post by wrightee on 2008-02-07
Uh oh... I won't be getting much done this afternoon then ;)  Thanks for the responses; I'm going to put the kettle on and dive in!

---

### Post by wrightee on 2008-02-07
I disgrace myself for chickening out on an SSH solution and went with a quick python hack run via a sudo'd php exec (we've got an internal webserver running on the box so it was just a matter of one line file that can be 'buttonized' on firefox's shortcut bar :) )

My python life is only one week old, so for your amusement:

#! /usr/bin/env python
import os
import re
vi,vo=os.popen4("amixer sget PCM")
if re.search(r'100%',vo.read()):volume="0%"
else:volume="100%"
os.system("amixer sset PCM "+volume)

... problem is now I'm going to have to hack a last.fm channel chooser, jquery powered volume slider and all the rest of it... 

Thanks for the help anyway!

---

### Post by lnostdal on 2008-02-07
hey, it's probably a better (=simpler) solution anyway :)

---

