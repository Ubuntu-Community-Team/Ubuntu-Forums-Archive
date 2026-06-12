---
title: "OpenGL fix, power consumption etc."
date: 2012-10-06
forum: New to Ubuntu
---

### Post by Grabbe on 2012-10-06
Hi! Since I'm a noob, though learning fast since I installed Ubuntu 12.04 LTS about two months ago, I want to ask all you amateurs and pros about a couple of things (one is pretty complicated):

1. Are there any good power-saving modes in Ubuntu that can be activated through plugins/programs? (Using a notebook)

2. How do I fast-switch between keyboard-layouts I use?

3. This is probably a bit more complex:

I've also got a problem with OpenGL, my Openarena won't start up:

GLimp_Init() - could not load OpenGL subsystem. See "/home/anonymous/.openarena/baseoa/crashlog.txt" for details.

The thing is that I've tried installing both the OpenGL-drivers? from Ubuntu Software Center and the stand-alone Nvidia drivers. But nothing worked. Helpz plx. :)

---

### Post by Grabbe on 2012-10-06
ioq3 1.36+svn2202-1/Ubuntu linux-x86_64 Dec 12 2011
Have SSE support
----- FS_Startup -----
Current search path:
/home/anonymous/.openarena/baseoa
/usr/lib/games/openarena/baseoa
/usr/lib/games/openarena/baseoa/pak6-patch085.pk3 (559 files)
/usr/lib/games/openarena/baseoa/pak6-misc.pk3 (229 files)
/usr/lib/games/openarena/baseoa/pak5-TA.pk3 (139 files)
/usr/lib/games/openarena/baseoa/pak4-textures.pk3 (1753 files)
/usr/lib/games/openarena/baseoa/pak2-players.pk3 (669 files)
/usr/lib/games/openarena/baseoa/pak2-players-mature.pk3 (231 files)
/usr/lib/games/openarena/baseoa/pak1-maps.pk3 (100 files)
/usr/lib/games/openarena/baseoa/pak0.pk3 (1042 files)

----------------------
4722 files in pk3 files
execing default.cfg
couldn't exec q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
Couldn't read q3history.
----- Initializing Renderer ----
Trying to load "renderer_opengl1_x86_64.so" from "/usr/lib/ioquake3"...
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----
SDL using driver "x11"
Initializing OpenGL display
Estimated display aspect: 1.779
...setting mode 3: 640 480
Available modes: '1366x768 1360x768 640x480 800x600 1024x768'
Couldn't get a visual
...WARNING: could not set the given mode (3)
Initializing OpenGL display
...setting mode 3: 640 480
Available modes: '1366x768 1360x768 640x480 800x600 1024x768'
Couldn't get a visual
...WARNING: could not set the given mode (3)
----- Client Shutdown (Client fatal crashed: GLimp_Init() - could not load OpenGL subsystem) -----
RE_Shutdown( 1 )
Hunk_Clear: reset the hunk ok
-----------------------
GLimp_Init() - could not load OpenGL subsystem

---

### Post by fyfe54 on 2012-10-06
For power consumption, try Jupiter.

[http://www.jupiterapplet.org/](http://www.jupiterapplet.org/)

Also, if you search the forums - there are many threads concerning power consumption.

---

### Post by Grabbe on 2012-10-06
OK! THX!

Only got the OpenGL-problem left. :)

---

### Post by akoskm on 2012-10-06
> **Grabbe said:**
> OK! THX!

Only got the OpenGL-problem left. :)

You mentioned that you downloaded nvidia drivers. Do you have graphics cards with optimus technology / hybrid graphics?
Additionally post the output of
```

lspci | grep VGA

```

---

### Post by Grabbe on 2012-10-06
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 105a (rev a1)

I've got an 'Nvidia 610M' I think. I mean, it SHOULD work with Openarena... lol.

---

### Post by akoskm on 2012-10-06
> **Grabbe said:**
> 00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 105a (rev a1)

I've got an 'Nvidia 610M' I think. I mean, it SHOULD work with Openarena... lol.

Yup, you are rolling with hybrid graphics.

Pick up [bumblebee]("https://wiki.ubuntu.com/Bumblebee") or ironhide (found no reliable wiki entry about ironhide and [this]("http://askubuntu.com/questions/121962/bumblebee-ubuntu-12-04-blender") askubuntu question).
[Bumblebee or Ironhide?]("http://askubuntu.com/questions/108648/bumblebee-or-ironhide")
I'm using bumblebee.

---

### Post by Grabbe on 2012-10-06
Got bumblebee, tried to run with:
optirun openarena
and
optirun hon

It goes black and doesn't work. :(

---

### Post by akoskm on 2012-10-07
Any output in the console, error message?

---

### Post by Grabbe on 2012-10-07
No, but I solved it. First I uninstalled all the nvidia drivers, then reinstalled bumblebee - installed all nvidia drivers and finally I used synaptics to install bumblebee-nvidia and it all works. :) Thx!

---

### Post by akoskm on 2012-10-07
> **Grabbe said:**
> No, but I solved it. First I uninstalled all the nvidia drivers, then reinstalled bumblebee - installed all nvidia drivers and finally I used synaptics to install bumblebee-nvidia and it all works. :) Thx!

The correct order would be uninstalling all the video drivers and installing only bumblebee-nvidia. This would pull you the rest of the packages. But you basically did the same thing, don't change once it works! :)

---

