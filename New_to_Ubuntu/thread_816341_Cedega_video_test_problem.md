---
title: "Cedega video test problem"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by ichimeno on 2008-06-02
Hey! I've recently installed linux on my pc because im tired of reformatting my Windows OS every two monthy. Currently, i'm loving Linux. Its real nice and pretty. =P But there is only one problem though that ive been trying to solve but without any luck. Since i like to play a lot of Online games i've gotten Transgaming Cedega and i've installed Guild Wars successfully but when i launch it a message pops up and says it cant initialize 3D output. So i ran a Video test and it appeared as Failed in the OpenGL part. I opened the terminal and typed int Glxinfo and this is what it showed:

name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x5c 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None



this is wierd because on my other computer it didnt have this type of problem. I can seem to fix it because i dont really know what this is. 
Has anyone had this problem before and knows how to fix this? 

Thank You in advance!

---

### Post by shifty_powers on 2008-06-02
if you go into the terminal and type

```
glxgears
```

what kind of score do you get?

and what grahpics card are you using?

---

### Post by ichimeno on 2008-06-02
this is what i get:

Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual



oh and im using a Nvidia GeForce 4 card

---

### Post by shifty_powers on 2008-06-02
hmm ok, what driver are you using for your graphiocs card?

---

### Post by ichimeno on 2008-06-02
im using nvidia and not nv.

---

### Post by shifty_powers on 2008-06-02
trying to remember if the geforce 4 cards use the legacy driver.

have you tried using envy?

```
sudo apt-get install envyng-gtk
```

is it an mmx by any chance

---

### Post by ichimeno on 2008-06-02
Did that.It said that its already installed.

---

### Post by shifty_powers on 2008-06-02
yeah, i checked, and the nvidia site says that card is supported in the unified driver.

is compiz working ok?

---

### Post by Maestro23 on 2008-06-02
Found an old thread over at the Cedega forums about Guild Wars (one of many). Don't know if you've seen it.

[http://www.cedega.com/forum/viewtopic.php?t=5264&highlight=nvidia+geforce+4](http://www.cedega.com/forum/viewtopic.php?t=5264&highlight=nvidia+geforce+4)

---

### Post by shifty_powers on 2008-06-02
kind of worried that glxgears didn't work mind.

what is the output of

```
glxinfo
```

and put it in code tags ;)

---

### Post by ichimeno on 2008-06-02
Here is the output of glxinfo:

name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x5c 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None


thnx Maestro ill check it out right now, =)


EDIT:

So ive typed: cat /proc/driver/nvidia/agp/status  and this is what i received:
Status: 	 Disabled


When i read the cedega theres a section where i didnt quit get:

1. Check your xorg.conf and see if you are properly using your glx drivers.

- For NVIDIA users, make sure the following are commented out:
Quote:

1. GLcore
2. dri 


Am i suppose to modify the xorg.conf file or should i like add these two thing below the driver section of the xorg.conf file?

---

