---
title: "'No available video device failed' and 'could not load OpenGL subsystem'"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by walawa on 2008-08-20
Hello,
I'm running Ubuntu Hardy and my graphics card is a 256mb nVidia e-GeForce 7100 GS with with the nVidia proprietary driver. When I try to run certain games I get these errors:

UrbanTerror:
```
ioQ3 1.35urt linux-i386 Jun 22 2008
----- FS_Startup -----
Going through search path...

----------------------
8032 files in pk3 files
execing default.cfg
execing q3config.cfg
execing autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
Couldn't read q3history.
----- Initializing Renderer ----
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1:
Calling SDL_Init(SDL_INIT_VIDEO)...
SDL_Init(SDL_INIT_VIDEO) failed: No available video device
failed
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem
```

FretsOnFire:
```
Traceback (most recent call last):
  File "./FretsOnFire.py", line 64, in <module>
    engine = GameEngine(config)
  File "/usr/share/games/fretsonfire/game/GameEngine.py", line 155, in __init__
    self.video.setMode((width, height), fullscreen = fullscreen, multisamples = multisamples)
  File "/usr/share/games/fretsonfire/game/Video.py", line 49, in setMode
    pygame.display.init()
pygame.error: No available video device
```

These games had been running fine until recently.

After doing a little research I found this post: [https://help.ubuntu.com/community/NvidiaTroubleshooting](https://help.ubuntu.com/community/NvidiaTroubleshooting), that proposed to add '+set r_gldriver libGL.so.1' after the command to solve opengl problems but I still get the same opengl errors. I haven't found anything about the SDL error or the others.

Can anyone help me solve this?

---

### Post by walawa on 2008-08-26
I solved it. The problem wasn't OpenGL, it was SDL. I had recently installed SDL from source without the development files which screwed up the configuration. So I uninstalled SDL through synaptic and installed the libsdl1.2-dev package. I then installed SDl from the source I got at their website ([http://www.libsdl.org/](http://www.libsdl.org/)). 

Although the games aren't bug-free they do startup and run decently enough.

---

