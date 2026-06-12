---
title: "Wanna 3d a retro game... help?!"
date: 2006-12-24
forum: Programming Talk
---

### Post by tocleora on 2006-12-24
I've always had this urge to see one of my favorite classic console games in a 3d environment.  I would like to know what tools I should use that would be the easiest and fastest to learn to create this... I'd prefer not to have to spend a lot of time learning a new language or piece of software, I'd rather invest that time in the game.  The quality of graphics can be as primitive as the original Wolfenstein 3D, it's obviously not something I want to market as I'm sure it would be complicated to get permission from the original creators.  I have experience programming in BASIC (including QB and VB) and PHP.  Please let me know everything I need, from creating the 3D world to whatever I would need to design the characters.  Hopefully it's all available for Ubuntu... and free... :)  Thanks in advance!

---

### Post by Wybiral on 2006-12-24
For 3d modeling... Blender is simple amazing. If you know python, you can also make simple games with python.

For a graphics API, OpenGL is the way to go.

If you want BASIC + 3d, there's Basic4SDL (check my sig) and freeBasic which are both free and linux compatible.

But, for the most control, I would suggest SDL + OpenGL.

---

### Post by tocleora on 2006-12-24
Ok, so I'm assuming I'm going the SDL + OpenGL path at this point.  I found these instructions a while back:

[http://ubuntu-gamedev.wikispaces.com/How-To+Setup+SDL+for+games+development](http://ubuntu-gamedev.wikispaces.com/How-To+Setup+SDL+for+games+development)

When installing all "libsdl" like it said, when I get to "libsdl-1.2dev" (which in synaptic is written "libsdl1.2-dev") I get this error:

```
libsdl1.2-dev:
 Depends: libglu1-mesa-dev but it is not going to be installed or
	libglu-dev
```

If I try to install libglu1-mesa-dev I get:

```
libglu1-mesa-dev:
  Depends: libglu1-mesa (=6.4.1-0ubuntu8) but 6.5.1+cvs20060824 is to be installed
 Depends: libgl1-mesa-dev but it is not going to be installed or
	libgl-dev
```

I have build-essentials and g++ installed.  

Any thoughts?

---

### Post by Wybiral on 2006-12-24
Hmm, I'm not entirely sure. On my system I have:

Mesa:
[LIST]
[*]libgl1-mesa-dev
[*]libgl1-mesa-dri
[*]libgl1-mesa-glx
[*]libglu1-mesa
[*]libglu1-mesa-dev
[/LIST]

SDL:
[LIST]
[*]libsdl1.2debian
[*]libsdl1.2debian-alsa
[*]libsdl-gfx1.2-4
[*]libsdl-gfx1.2-4-dev
[*]libsdl-image1.2
[*]libsdl-image1.2-dev
[/LIST]
And them some SDL network, font, and media stuff which isn't really important.

And everything installed just fine.

Those are really the most important packages for using OpenGL and SDL with C/C++ (unless I left something out, but I think I covered them)

BTW, both links in my sig are related to OpenGL development. If you like BASIC, Basic4SDL is an ubuntu-friendly interpreted BASIC language with SDL and OpenGL wrapping. Viper is an OpenGL toolkit for python and it only requires python and pyOpenGL to make games and stuff. Both of them come with examples too. Maybe worth a look to see some OpenGL code in action.

---

### Post by tocleora on 2006-12-24
Ok I got it, I was using a csv version of one of the files and then turned off the respository that supplied it so dev was wanting an older version than I have installed.  I'll post more later with my efforts from here...

---

### Post by protasenko on 2006-12-28
I had exact same problem. Here's how it's fixed:
su
apt-get update
apt-get install --reinstall libglu1-mesa/edgy

At this point libsdl-dev shouldn't complain:
apt-get install libsdl-dev

---

