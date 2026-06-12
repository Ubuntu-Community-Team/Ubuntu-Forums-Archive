---
title: "Looking for FAQs, Tuts for an experienced Win programmer.."
date: 2006-04-09
forum: Programming Talk
---

### Post by benfinkel on 2006-04-09
Hey All,

I fired up Ubuntu(GNOME) recntly and I want to get to some programming.  I'm a fairly experienced Win32 programmer, having programmed in C/C++/VB/.NET/SQL Server/etc... for about ten years.

What I don't know anything about is the *nix architecture?  What is SDL, GTK, how do I move from simple TTL programming to GNOME/KDE apps?  I've looked at the GLADE website, the screenies look nice, but how are they integrated with a C program in *nix?  Do I need to know anything about X, or does GNOME cover that for me?

So, I was hoping there were some resources out there that would help introduce me to these concepts.  Maybe even learn me the right questions to ask :)

Thanks all!

-Ben

---

### Post by dolson on 2006-04-09
GTK is the Gimp Toolkit, it's what all the GNOME apps use to draw the widgets, like buttons, comboboxes, etc. Glade is a GUI designer app for GTK. You can load a .glade file into your C/C++ or whatever language you want and then you connect signals and such.. Hard for me to explain, but basically, you're on the right track. Look at Anjuta for a decent IDE.

Here's a bit of a tutorial for you to check out:
[http://gtk.org/tutorial/](http://gtk.org/tutorial/)

That should get you on the right track. :)

KDE uses the Qt toolkit. You can run GTK apps on KDE and Qt apps on GNOME. So choose whichever you like. I prefer GTK myself (although I haven't developed anything beyond a simple hello world app with it yet).

SDL is what I do my development in. It's a library, kinda like DirectX is, for graphics, mouse/keyboard/joystick input, etc. OpenGL is what you use in place of DirectX. You can get add-on libs such as SDL_net for networking, SDL_image for image file loading, SDL_mixer for sound, OpenAL for advanced sound, and so on. SDL is usually used for games (and many commercial ports use it as well, and some commercial Windows games do as well).

Hope that helps you out a bit.

---

### Post by benfinkel on 2006-04-09
Dolson,

Thanks for the quick reply.  That does help out quite a bit, I appreciate it! :-D 


You mentioned SDL and OpenGL both as replacements for DirectX.  As I understand it OpenGL is really the "equivalent" for the graphics libraries of DirectX and SDL is the "equivalent" of the other stuff (like you said, input/networking/image manip/etc...).  I put equivalent in quotes because I realize none of these things are direct replacements.

Also, I d/l'ed Kdevelop, since I heard many good things about it.  I'll grab Ajunta as well, but I'm not looking for terribly much in an IDE.  Some color coding and collapsable code and decent project file managment is about all I need.

Thanks for the pointers, I'm looking forward to this!  Hoepfully I can break something soon! :evil:

---

### Post by dolson on 2006-04-09
Well, Kdevelop is going to be geared more towards Qt/KDE apps.

Anjuta (for me) is a direct replacement for Visual C++. I haven't used Kdevelop in years, but Anjuta is great. I think you'd want to stick with GTK apps if you're developing with GTK.

Just run sudo apt-get install anjuta if you want to download and install it. Or use Synaptic. :)

OpenGL is for 3D (generally) and SDL does 2D only. They do work hand-in-hand though. Just search for an OpenGL/SDL tutorial and you'll see that a lot of the OpenGL stuff is made easier with SDL.

---

### Post by benfinkel on 2006-04-09
Coolness.  Thanks again.


Does Ubuntu come pre-installed with all of the GTK libraries if I want to get started programming GTK right away or do I need to d/l the source and compile it myself?

Thanks again!

---

### Post by wmcbrine on 2006-04-09
[QUOTE=benfinkel]Does Ubuntu come pre-installed with all of the GTK libraries if I want to get started programming GTK right away or do I need to d/l the source and compile it myself?[/QUOTE]Neither... the needed packages aren't installed by default, but you can grab them via Synaptic or apt-get.

Can I just add that Glade rocks. :-)

---

