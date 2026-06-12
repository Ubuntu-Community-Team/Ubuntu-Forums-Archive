---
title: "Bad file descriptor"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by Cale Collins on 2008-05-20
I'm trying to get my Ati card configured. I watched a you tube video called 

Ubuntu 7.10 Bonus Material: Video and 3D Cube (Part 2) [http://www.youtube.com/watch?v=QwI6YsQd4qI](http://www.youtube.com/watch?v=QwI6YsQd4qI)

After installing Envy I tried to initialize my card, a HD2600xt made by Visiontek

Using Terminal, I type the line ATIConfig --initial 
the following code is:

Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-0
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.

After I type the line:

cale@Supercompuer:~$ aticonfig --initial=check
Check: No fglrx section.

Meaning to me the driver is not loaded.

What should I do to resolve this?

This is the second day I have had Ubuntu installed,  And I am a first time linux user, also I am new to the forums.

---

### Post by Cale Collins on 2008-05-20
Bump

---

