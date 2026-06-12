---
title: "fullscreen videos and other applications on a new X server"
date: 2006-08-14
forum: Outdated Tutorials &amp; Tips
---

### Post by reda_ea on 2006-08-14
One thing I didn't like about XGL is fullscreen videos...

XV dosen't work well and GL2 is too slow .. the only option I had is running a new session with a normal server and running the video there

The same goes for OpenGL games and applications.

So I made this very little script (xmplayer) that runs mplayer fullscreen on a new Xorg server, taking care of all the authorization stuff (this assumes you're not using display :13, if you are you should modify the script).

To control the video just press 'f' to disable full screen .. or learn the shortcuts (in the man).
[ATTACH]14277[/ATTACH]

To use this with nautilus I put xmplayer in /opt and added an application to the gnome menu, something like this screenshot
[ATTACH]14278[/ATTACH]
and I just used "open with.." dialog and now it works just fine.

Another more generic script is nxrun witch runs any given command on a new server.
Probably the best is to use that script and modify it to create launchers for many applications and in many displays.

---

### Post by abrichr on 2007-07-26
this would be great if it worked for feisty.  any chance for an updated version?

---

### Post by reda_ea on 2007-09-19
sorry I always thaught this thread was never posted, so I never got back to it
I'll have a look at this as soon as I have some time

---

