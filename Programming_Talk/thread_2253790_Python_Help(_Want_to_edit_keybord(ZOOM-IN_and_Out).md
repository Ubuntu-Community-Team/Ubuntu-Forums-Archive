---
title: "Python Help( Want to edit keybord(ZOOM-IN and Out) shortcut of Gimp)"
date: 2014-11-22
forum: Programming Talk
---

### Post by Hasibuzzaman_Chowd on 2014-11-22
I have used a keybord shortcut changeing file(Python code) for gimp2.8+ , This file made my Gimp shortcut as like Photoshop. I need to change the ZOOM-In  fuction's shortcut to be  (Cntrl+Space+Right Mouse Click) and ZOOM-OUT to be (Cntrl+alt+Space+Right Mouse Click). I am not a programmer, So , Request to python programmers ,can you please help me by editing this code .

The file can be found from the link velow .
[http://epierce.freeshell.org/gimp/ps-menurc](http://epierce.freeshell.org/gimp/ps-menurc)

Thanks,
Hasib

---

### Post by ofnuts on 2014-11-22
You can't do it with a plugin (which is what you can use Python for in Gimp)... You would need to go rather deep in the keyboard handling in C and recompile your own Gimp version because the spacebar is used for the "pan" function which is always active. You can use "Edit>Keyboard short cuts" to set Zoom-in and Zoom-out to Ctrl-Space and Ctrl-Alt-Space, without the mouse click.

As a seasoned Gimp user I wonder why you would want such a strange setup when Ctr-Mousewheel does the same thing with any decent mouse.

PS: looked at the file and this isn't python code. This is just the Gimp configuration file for the keyboard shortcuts (that looks a bit like Lisp syntax).

---

