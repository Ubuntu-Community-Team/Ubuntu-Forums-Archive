---
title: "Moving out of the Terminal"
date: 2007-03-29
forum: Programming Talk
---

### Post by projectgonewrong on 2007-03-29
Okay I have been doing C++ for like a year and a half and have been TI (calculator) programming for over 2 years. I can do pretty much anything in C++ in the Terminal  window.

But how do I make windows and such, I know its a pretty broad question. The Terminal window is kinda lame. So anyways how do you get out of the dumb Terminal and make a window.  Like some example code or tutorials or something?

---

### Post by Wybiral on 2007-03-29
Have you tried using a library like ncurses with the terminal to make your stuff a little more graphical?

What kind of windows? GUI's like applications have, or graphical windows like games?

Either way, the key is to find a good library for it. GTK is pretty popular for GUI's, and SDL is pretty popular for games.

---

### Post by lnostdal on 2007-03-29
[http://www.gtk.org/tutorial/](http://www.gtk.org/tutorial/)
[http://www.gtk.org/api/](http://www.gtk.org/api/) (in particular [http://developer.gnome.org/doc/API/2.0/gtk/index.html](http://developer.gnome.org/doc/API/2.0/gtk/index.html) )

```

sudo aptitude install gnome-core-devel

```

..remember to use pkg-config when compiling/linking as described in the GTK+ tutorial.

edit:
i think we posted at the same time (below)

---

### Post by projectgonewrong on 2007-03-29
nevermind, he posted while I was responding to first guy.

---

### Post by thethawav on 2007-03-29
I'd consider using GTKmm in combination with C++ (gtk enhanced by c++ bindings)

---

### Post by projectgonewrong on 2007-03-29
How do I set up SDL? Like is there a terminal command to get it?

---

### Post by lnostdal on 2007-03-29
```
aptitude search libsdl | grep dev
```

---

### Post by projectgonewrong on 2007-03-29
This is the result:

wesley@ubuntu:~$ aptitude search libsdl | grep dev
E: /home/wesley/.aptitude/config - Unable to open %s for writing (13 Permission denied)
p   libsdl-console-dev              - development files for libsdl-console      
v   libsdl-dev                      -                                           
p   libsdl-gfx1.2-dev               - development files for SDL_gfx             
p   libsdl-image1.2-dev             - development files for SDL 1.2 image loadin
p   libsdl-mixer1.2-dev             - development files for SDL1.2 mixer library
p   libsdl-net1.2-dev               - Development files for SDL network library 
p   libsdl-ocaml-dev                - OCaml bindings for SDL - development files
p   libsdl-sge-dev                  - development files for libsdl-sge          
p   libsdl-sound1.2-dev             - Development files for SDL_sound           
p   libsdl-stretch-dev              - Development files for SDL_stretch library 
p   libsdl-ttf1.2-dev               - development files for libsdl-ttf1.2       
p   libsdl-ttf2.0-dev               - development files for SDL ttf library (ver
p   libsdl1.2-dev                   - Simple DirectMedia Layer development files

How do I fix this problem?

---

### Post by Wybiral on 2007-03-29
If you want OpenGL too, I explained how to get SDL and OpenGL here: [http://www.ubuntuforums.org/showthread.php?t=395396](http://www.ubuntuforums.org/showthread.php?t=395396)

If not, just omit the OpenGL related stuff.

---

### Post by lnostdal on 2007-03-29
just do ```
sudo aptitude install libsdl-dev
```

---

### Post by projectgonewrong on 2007-03-29
Where do I get "SDL/SDL_ttf.h" is there something I can type in Terminal to get it.

---

### Post by Wybiral on 2007-03-29
I would suggest searching either google or synaptic... Synaptic is a better choice.

Thats the ttf font extension for SDL.

Here's the command to install them
```

sudo apt-get install libsdl-ttf2.0-0 libsdl-ttf2.0-dev

```

Although a quick search in your package manager would have brought them up...

---

### Post by projectgonewrong on 2007-03-30
Oh I only did one of those earlier it works now thanks.

---

