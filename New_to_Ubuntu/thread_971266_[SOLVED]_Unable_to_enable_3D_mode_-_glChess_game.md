---
title: "[SOLVED] Unable to enable 3D mode - glChess game"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by justchange on 2008-11-04
Just poking around in my first Ubuntu installation... was trying to play glChess game included in GNOME-games with 8.10.

I noticed an option "View>3D CHess View" and thought it would be interesting.

When I select it, I get the error: "Unable to enable 3D mode" (See attached image)
And "**No Python OpenGL support**" and "**No Python GTKGLExt support**".

I looked through Synaptic and didn't see anything obvious there.
What am I missing?

The system is AMD64 3200+, 512MB, 160GB, MSI-7191 m/b with onboard ATi X200 graphics. (I know it's not wonderful, but it runs everything Compiz-Fusion throws at it.)

Be gentle, ok... though I'm not a total nUUb... I've been using Ubuntu for a whole week, now. :D

Thanks!

---

### Post by fooman on 2008-11-04
have you installed your video drivers?

if not,  go to system > administration > hardware drivers

you should see the ati drivers available there,  click on it to enable/install the drivers,  then try the game again.

---

### Post by drewcoon on 2008-11-04
in terminal, do

```
sudo apt-get install python-opengl python-gtkglext1
```

that should get it working.

it's not a driver problem, it's some Python bindings that aren't installed. I just tried playing in 3D and got an identical message, installed these packages and it works fine now :)

---

### Post by praveenpious on 2008-11-04
^^ thanks for the info :)

---

### Post by justchange on 2008-11-04
Thanks for the solution, *drewcoon*.
I get the 3D now (it comes and goes, but I think that's more due to my weak system and the demands I'm putting on it... just to find out what it can do.)

This fix also helped with Google SketchUp (a free 3D modelling app) in Wine (it crashed immediately before, complaining of no openGl. Now, it runs a little farther before it crashes. :D )

Anyway, thanks a lot!

And Fooman, thanks for the response, too.
I've already gotten the updated ATi drivers for this chipset. (But it's well-noted for it's Linux struggles.)

---

