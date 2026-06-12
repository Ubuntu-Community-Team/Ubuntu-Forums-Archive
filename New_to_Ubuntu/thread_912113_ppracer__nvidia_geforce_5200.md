---
title: "ppracer / nvidia geforce 5200"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by roscopico on 2008-09-06
Hi all.

I'm trying to install ppracer for my daughter.

on start, monitor indicates "out of range".

Is this a problem w/ my video card?

natty@natty-desktop:~$ glxinfo | grep "render"
direct rendering: Yes
OpenGL renderer string: GeForce FX 5200/AGP/SSE/3DNOW!
natty@natty-desktop:~$ 


Stumped.

Any advice is appreciated.

---

### Post by Bloch on 2008-09-06
I have the graphics card

```
direct rendering: Yes
OpenGL renderer string: GeForce FX 5200/AGP/SSE2
```

When I start ppracer and change the resolution to 800x600 the screen blanks with the message
Cannot display this video mode
and I have to reboot.

The change to video mode 800x600 is stored in the file /.ppracer/options
(files beginning with a dot are hidden files)
You can change there to 1024x768 or something.


I don't like Planet Penguin Racer anyway. It is very very very difficult to advance to the next level (there is a thread on this somewhere). It's OK for kids to play around with for 20 minutes or so, but the upper levels are a waste of design.

---

### Post by roscopico on 2008-09-06
Thank you for the advice.

---

### Post by roscopico on 2008-09-06
The solution:  in the options file, "fullscreen" was set to "true".  I changed and now we're golden!
```

# fullscreen
#
# If true then the game will run in full-screen mode.
#
set fullscreen false

```
Thanks again!

---

