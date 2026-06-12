---
title: "OpenGL Programming"
date: 2007-01-10
forum: Programming Talk
---

### Post by but99007 on 2007-01-10
I am working on a project for school and need to do a lot of programming in C++ using OpenGL.  I am having trouble getting started and was wondering if any help was available.  I am running Kubuntu edgy and have installed mesa, and freeglut.  I also ran a script I found called Envy.  I can get a sample program to compile but when I run it I get the following error:
freeglut (./run): OpenGL GLX extension not supported by display ':0.0'

If I type glxinfo I get the following:
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


Is there something I did wrong?  How can I get this up and running as painlessly as possible?  I am a little new still so excuse my lack of knowledge.

Thanks

---

### Post by Grey on 2007-01-10
Your graphics card is not set up properly.  What kind of card do you have?

---

### Post by jblebrun on 2007-01-10
It looks like the GLX module isn't enabled. In your /etc/X11/xorg.conf, look for a section called Modules, and add the line Load "GLX" to it. Like this:

```

Section "Modules"
<you'll probably see other module load statements there already>
     Load   "GLX"
EndSection

```

---

### Post by jblebrun on 2007-01-10
On a side note, if you haven't already, check out these kick-*** tutorials:
[http://nehe.gamedev.net/](http://nehe.gamedev.net/)

They helped me to no end when I was taking a graphics class a few years back.

---

### Post by but99007 on 2007-01-11
This is what was already in my xorg.conf file.  So it looks like it is already loading GLX.

Section "Module"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

---

### Post by but99007 on 2007-01-11
Thanks for the link to NeHe, it looks like it will be a lot of help.

---

### Post by but99007 on 2007-01-11
As for what graphics card I have, it looks like I have an Intel 915 but there is also something about i810 as being the driver for it.

---

### Post by Ben Sprinkle on 2007-01-11
I have Intel 900 at the i810 driver. Works fine for my laptop. :)

---

### Post by tpg on 2007-01-11
I'd recommend using SDL as a wrapper for OpenGL. See [Ubuntu Gamedev]("http://ubuntu-gamedev.wikispaces.com/How-To+Setup+SDL+for+games+development") for more info.

---

### Post by Grey on 2007-01-11
I have the same video in my laptop.  The i810 drivers work fine, and I have good 3D acceleration.  You should not be having that problem.

Try running "glxgears" from the terminal, and tell me what it does.

Also, if you could post your entire xorg.conf, maybe we can see what is going on.  It looks like the driver is not being loaded properly at any rate.

Also, the output from "glxinfo" would be helpful.

---

