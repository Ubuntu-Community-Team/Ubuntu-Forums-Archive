---
title: "Intel graphic drivers"
date: 2015-01-28
forum: New to Ubuntu
---

### Post by test11 on 2015-01-28
Hi,

I'm new to ubuntu and linux. I would like to test wayland with phoronix (openarena test) but it crashes on start up.
I found the crash log and I would like if someone could explain the log to me.
And after that if he or she could help me to fix it.

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)

[ATTACH]259568[/ATTACH]
```
 ioq3+oa 1.36_SVN1910M linux-x86_64 Dec 25 2011----- FS_Startup -----
Current search path:
/root/.phoronix-test-suite/installed-tests/pts/openarena-1.5.2///.openarena/baseoa
./baseoa/pak6-patch088.pk3 (711 files)
./baseoa/pak6-patch085.pk3 (559 files)
./baseoa/pak6-misc.pk3 (229 files)
./baseoa/pak5-TA.pk3 (139 files)
./baseoa/pak4-textures.pk3 (1753 files)
./baseoa/pak2-players.pk3 (669 files)
./baseoa/pak2-players-mature.pk3 (231 files)
./baseoa/pak1-maps.pk3 (100 files)
./baseoa/pak0.pk3 (1042 files)
./baseoa


----------------------
5433 files in pk3 files
execing default.cfg
execing q3config.cfg
com_zoneMegs will be changed upon restarting.
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
Couldn't read q3history.
----- Initializing Renderer ----
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----
SDL using driver "fbcon"
Initializing OpenGL display
Estimated display aspect: 1.779
...setting mode 3: 640 480
Available modes: '1366x768 320x200 640x400 320x240 512x384 640x480 768x576 800x600 960x720 1024x768'
Couldn't get a visual
...WARNING: could not set the given mode (3)
Initializing OpenGL display
...setting mode 3: 640 480
Available modes: '1366x768 320x200 640x400 320x240 512x384 640x480 768x576 800x600 960x720 1024x768'
Couldn't get a visual
...WARNING: could not set the given mode (3)
----- Client Shutdown (Client fatal crashed: GLimp_Init() - could not load OpenGL subsystem
) -----
RE_Shutdown( 1 )
-----------------------
GLimp_Init() - could not load OpenGL subsystem
```
Thank you

---

### Post by deadflowr on 2015-01-29
I added your output from the txt file so people won't have to download it.
always better to post directly in the thread when possible. 
(Simply copy and paste it, use ```
 tags --the # symbol in the reply to thread and adv reply options)
Of course if the output is extremely long, then best is linking to a [pastebin]("https://help.ubuntu.com/community/Pastebinit").


That said you seem to be having an OpenGL problem, 

However the output, I assume, from the lspci for the VGA line seems like it's a little too generic.
I would think you would at least see more about which particular intel graphics card it is...
I think
[code]sudo lshw -c display
```
might give you more about the card...

Intel drivers are all open-source only, but intel does produce newer drivers which have support for newer hardware, which may not have been made available at the time of your Ubuntu's version released.

---

