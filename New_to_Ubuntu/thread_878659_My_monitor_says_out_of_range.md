---
title: "My monitor says out of range"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by oDEIMOSo on 2008-08-03
My monitor says out of range on some video games i try to play like Open Arena and Aliens vs Predator , what can i do to fix this problem .

---

### Post by Sirron on 2008-08-03
It may be that the games are set, by default, to a resolution higher than the native resolution of your monitor.

You can usually change it, by editing the config file for the game - usually found in your home folder, under a hidden folder named after the program.

Alternatively, it could be that the refresh rate is set too high/low in the game, you can often change that in the same way. Set it to 60Hz.

---

### Post by oDEIMOSo on 2008-08-03
ok ill try that thanks

---

### Post by oDEIMOSo on 2008-08-03
Ok I know this is gonna sound dumb , but im new at this and i went to my home folders and there wasnt anything like that in there , Is there anywhere else the folder could be in ?

---

### Post by oDEIMOSo on 2008-08-03
Ok nevermind i found the file in my wine drive file . But wich one to i change and how do I do that ?

---

### Post by Sirron on 2008-08-03
It'll be a hidden folder, so show hidden folders by clicking "View", then "Show Hidden Files". Alternatively, use the keyboard shortcut, "Ctrl+H".

These folders start with a "." so you'll be looking for .alien-arena

in that you'll see "arena" and in that you'll see config.cfg

Try editing that. If you ever mess up a config file fiddling with it in this way, you can really just delete it, and the program will generate a new one when you start the game again.

I assume changing:

set vid_height "1050"
set vid_width "1680"

to your native resolution will do the trick.

---

### Post by Sirron on 2008-08-03
Ohhh, sorry I didn't know you were using wine. I should point out, Alien Arena is available as a native linux build and works fine.

click [apt:alien-arena]("apt:alien-arena") to install it if you like.

---

### Post by oDEIMOSo on 2008-08-03
I`m only using wine for Alien vs Predator , The other game that im having problems with is Open Arena , I found Open Arena`s file and changed it but i cant find the alien vs predator ! But the problem i`m having is i got a good system but i got a small monitor , so i don`t know how to change the resolution past 1024 x 786 so I dont really know what to change it to on the games !

---

### Post by oDEIMOSo on 2008-08-03
I`ve changed the resolution twice for Open Arena but it still gives me the same out of range thing on my monitor . I dont understand it dosn`t do that that on assault cube or alien arena . Why does it do that on open arena ?

---

### Post by Bradtek on 2008-08-03
I have seen the "out of range error"
when I set my Refresh Rate too high.


I guess the Refresh Rate setting would be 
in the same config file.

AFAIK most monitors work at 60 Hz

My crappy old Dell 17" CRT does up to 
85 Hz at 1024 X 768 or
75 Hz at 1152 X 864

---

### Post by philinux on 2008-08-03
[http://openarena.wikia.com/wiki/FAQ#How_to_change_the_video_resolution_to_widescreen_1680x1050.2C_1280x800_or_anything_else_.3F](http://openarena.wikia.com/wiki/FAQ#How_to_change_the_video_resolution_to_widescreen_1680x1050.2C_1280x800_or_anything_else_.3F)

from their wiki.

The file is in your home folder so change the vi bit to ~/.filename

---

