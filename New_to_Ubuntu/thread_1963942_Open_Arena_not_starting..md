---
title: "Open Arena not starting."
date: 2012-04-22
forum: New to Ubuntu
---

### Post by Greg Panaccione on 2012-04-22
I just recently downloaded Open Arena, and when I tried to play it, I got the error saying: > GLimp_Init() - could not load OpenGL subsystem
When I tried loading it from the terminal, I got this...

> gregory@gregory-K53SV:~$ openarena
ioq3 1.36+svn1946-5/Ubuntu linux-x86_64 Aug  9 2011
----- FS_Startup -----
Current search path:
/home/gregory/.openarena/baseoa
/usr/lib/games/openarena/baseoa/pak6-patch085.pk3 (559 files)
/usr/lib/games/openarena/baseoa/pak6-misc.pk3 (229 files)
/usr/lib/games/openarena/baseoa/pak5-TA.pk3 (139 files)
/usr/lib/games/openarena/baseoa/pak4-textures.pk3 (1753 files)
/usr/lib/games/openarena/baseoa/pak2-players.pk3 (669 files)
/usr/lib/games/openarena/baseoa/pak2-players-mature.pk3 (231 files)
/usr/lib/games/openarena/baseoa/pak1-maps.pk3 (100 files)
/usr/lib/games/openarena/baseoa/pak0.pk3 (1042 files)
/usr/lib/games/openarena/baseoa

----------------------
4722 files in pk3 files
execing default.cfg
couldn't exec q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
Couldn't read q3history.
----- Initializing Renderer ----
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
----- Client Shutdown (Client fatal crashed: GLimp_Init() - could not load OpenGL subsystem
) -----
RE_Shutdown( 1 )
-----------------------
GLimp_Init() - could not load OpenGL subsystem

I am fairly new to Linux, so any help would be appreciated greatly. Thank you all!

---

### Post by Greg Panaccione on 2012-04-23
I just recently downloaded Open Arena, and when I tried to play it, I got the error saying: > GLimp_Init() - could not load OpenGL subsystem
When I tried loading it from the terminal, I got this...

> gregory@gregory-K53SV:~$ openarena
ioq3 1.36+svn1946-5/Ubuntu linux-x86_64 Aug  9 2011
----- FS_Startup -----
Current search path:
/home/gregory/.openarena/baseoa
/usr/lib/games/openarena/baseoa/pak6-patch085.pk3 (559 files)
/usr/lib/games/openarena/baseoa/pak6-misc.pk3 (229 files)
/usr/lib/games/openarena/baseoa/pak5-TA.pk3 (139 files)
/usr/lib/games/openarena/baseoa/pak4-textures.pk3 (1753 files)
/usr/lib/games/openarena/baseoa/pak2-players.pk3 (669 files)
/usr/lib/games/openarena/baseoa/pak2-players-mature.pk3 (231 files)
/usr/lib/games/openarena/baseoa/pak1-maps.pk3 (100 files)
/usr/lib/games/openarena/baseoa/pak0.pk3 (1042 files)
/usr/lib/games/openarena/baseoa

----------------------
4722 files in pk3 files
execing default.cfg
couldn't exec q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
Couldn't read q3history.
----- Initializing Renderer ----
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
----- Client Shutdown (Client fatal crashed: GLimp_Init() - could not load OpenGL subsystem
) -----
RE_Shutdown( 1 )
-----------------------
GLimp_Init() - could not load OpenGL subsystem

I am fairly new to Linux, so any help would be appreciated greatly. Thank you all!

---

### Post by audiomick on 2012-04-23
I haven't used the program in question, but you error message indicates a problem with the video, I think.

On this manual page
[http://openarena.wikia.com/wiki/Manual/Install]("http://openarena.wikia.com/wiki/Manual/Install")

I noticed this comment
```
NOTE: You must have accelerated drivers for your video card installed for best results. This may require using the not-entirely-open-source NVIDIA drivers for NVIDIA cards. This also means that some video cards may not work even if they meet the above-stated minimum requirements. 
```

Have you checked to see if there are proprietary drivers for your graphics card?

---

### Post by mörgæs on 2012-04-23
Please don't double-post.
Merged.

---

### Post by Greg Panaccione on 2012-04-23
I did supposedly install the drivers, but then I got this message.

> You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

I can run the program from the terminal fine, but I have no clue how to restart the x server.

---

### Post by Greg Panaccione on 2012-04-23
Whoops never mind on that one... Just ran the program again and got this...

> gregory@gregory-K53SV:~$ sudo nvidia-xconfig
[sudo] password for gregory: 

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Default Device" must have a Driver line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'



Any idea as to what to do?

---

### Post by audiomick on 2012-04-23
Log off and log back on again, and see if it works now. There is a new Xorg.config there which the install will use when you log back on. Hopefully, it should work.

The easiest way to restart the X server is just to log off and log back on again. There is a terminal command for that, but I can never remember it. ;) If you are unsure, reboot.

---

### Post by Greg Panaccione on 2012-04-24
Tried it. After the failed log off, my computer shut off, and I had to re-load ubuntu -_- apparently I did something wrong. So very wrong... lol

---

