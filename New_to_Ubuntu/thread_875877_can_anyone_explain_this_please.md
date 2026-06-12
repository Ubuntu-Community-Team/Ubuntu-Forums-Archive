---
title: "can anyone explain this please"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by muted1987 on 2008-07-31
Loading OpenGL driver libGL.so.1
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Couldn't get an RGB, Double-buffered, Depth visual


 i get this when trying to run nexuiz anyone know how to correct this?

---

### Post by JaredLeto on 2008-07-31
not sure but it may have something to do with your video card driver. Try to install newest driver. (maybe this will fix your problem)

---

### Post by muted1987 on 2008-07-31
hey there is only the legacy driver for my card nvidia 440mx 

reinstalled but same error

---

### Post by JaredLeto on 2008-07-31
you could try to reinstall nexuiz with synaptic.

---

### Post by philinux on 2008-07-31
In a terminal use

glxinfo

Just paste back the first 40 or so lines.

---

### Post by muted1987 on 2008-07-31
> **JaredLeto said:**
> you could try to reinstall nexuiz with synaptic.

this might be worth a try but is there a way to change the install directory in synaptic as i need it on my data hdd not in the filesystem so to speak

---

### Post by JaredLeto on 2008-07-31
> **muted1987 said:**
> this might be worth a try but is there a way to change the install directory in synaptic as i need it on my data hdd not in the filesystem so to speak
i don`t think it`s possible. It will install nexuiz into /usr/games/

---

### Post by muted1987 on 2008-07-31
@ philinux i dont have that installed and i cant at the minute as im downing nexius 

@JaredLeto looks like ill save it there for now

---

### Post by muted1987 on 2008-07-31
ok so after installing from synaptic i get a box that comes up and keeps flashing would this be a compiz problem and if so how do i turn it off i am running xubuntu



@philinux this is result of glxinfo

root@jordan-desktop:/mnt/data/jordan/Nexuiz# glxinfo
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

---

### Post by philinux on 2008-07-31
What shows up under System>admin>Hardware Drivers.

You might want to click the report button on your first post and ask the moderators to change the title of this thread to something like.

Nvidia 440mx Graphics card problem and nexuiz.

---

