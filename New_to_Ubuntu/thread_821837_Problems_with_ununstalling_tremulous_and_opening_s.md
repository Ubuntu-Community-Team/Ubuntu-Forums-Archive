---
title: "Problems with ununstalling tremulous and opening synaptic package manager"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by drksolo12 on 2008-06-07
:confused: plz someone help i just got ubuntu for the first time and now im stuck 
i got tremulous and it didnt work so i wanted to uninstall it so what i did is i went to add or remove programs and tried uninstallign tremulous and a message came up and tremulous doesnt uninstall and that same message comes up when i open synaptic package manager and then synaptic package manager closes when i press ok the missage is>  E:dpkg was interrupted,you must manually run dpkg--configure-a'to correct the problem.
E:_cache->open()failed,please report


plz help and if you find a solution please in detail im not even 16!

---

### Post by Happy_Man on 2008-06-07
Open up a terminal (Applications --> Accessories --> Terminal) and enter this line:

```
sudo dpkg --configure -a
```

And, like the error message says, it should correct the problem.

---

### Post by drksolo12 on 2008-06-07
tyyyyyyyyyyy soooooo much ur a pc god!:guitar: but i still have one problem its tremulous i really wanan play it so here goes
i got tremulous and i cant play it cuz when i click on it i see a black screen for 1 second(s) and then tremulous switches off i tried it on the terminal and umm it coems up with a message
> tremulous 1.1.0 linux-x86 Jun 16 2007
----- FS_Startup -----
Current search path:
/home/farhan/.tremulous/base
/usr/share/games/tremulous/base/vms-1.1.0.pk3 (4 files)
/usr/share/games/tremulous/base/map-uncreation-1.1.0.pk3 (110 files)
/usr/share/games/tremulous/base/map-tremor-1.1.0.pk3 (45 files)
/usr/share/games/tremulous/base/map-transit-1.1.0.pk3 (135 files)
/usr/share/games/tremulous/base/map-niveus-1.1.0.pk3 (134 files)
/usr/share/games/tremulous/base/map-nexus6-1.1.0.pk3 (151 files)
/usr/share/games/tremulous/base/map-karith-1.1.0.pk3 (118 files)
/usr/share/games/tremulous/base/map-atcs-1.1.0.pk3 (87 files)
/usr/share/games/tremulous/base/map-arachnid2-1.1.0.pk3 (67 files)
/usr/share/games/tremulous/base/data-1.1.0.pk3 (1229 files)
/usr/share/games/tremulous/base
/usr/lib/tremulous/base

----------------------
2080 files in pk3 files
execing default.cfg
couldn't exec autogen.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----

------- Input Initialization -------
Joystick is not active.
------------------------------------
...loading libGL.so.1:
Calling SDL_Init(SDL_INIT_VIDEO)...
SDL_Init(SDL_INIT_VIDEO) passed.
Initializing OpenGL display
...setting mode 3: 640 480
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
Using 8/8/8 Color bits, 16 depth, 8 stencil display.
GL_RENDERER: Mesa GLX Indirect


***********************************************************
 You are using software Mesa (no hardware acceleration)!   
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
...WARNING: could not set the given mode (3)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem
 some one plz help i a kid in need and i aprreciate your help all of you thank you!:lolflag:

---

### Post by Happy_Man on 2008-06-07
You don't have the proper video driver installed. To remedy this, go to System --> Administration --> Hardware Drivers and enable the video driver there, if one is available for your card. If not, well, sorry :( .

---

