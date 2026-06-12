---
title: "How do I install my own screensaver?"
date: 2007-10-08
forum: Programming Talk
---

### Post by pkfx on 2007-10-08
I made a fullscreen SDL/OpenGL application that I would like to use as a screensaver. The application runs fine, but I'm having trouble getting it to run as a screensaver. Does anyone know how to do this?

I'm using Ubuntu Feisty Fawn with Gnome Screensaver. I was able to get some information about installing screensavers [at this website]("http://www.gnome.org/learn/admin-guide/latest/screensavers-3.html"). The .desktop files for all of the screensavers are located in /usr/share/applications/screensavers. The screensavers that come with Gnome Screensaver are located in /usr/lib/gnome-screensaver/gnome-screensaver. I copied my application to that directory and making a .desktop file for my screensaver by duplicating one of the others and editing that. When I go into Screensaver Preferences I can see the name of my screensaver in the list but it never actually executes. I just get a blank screen.

Any ideas would be greatly appreciated. Thanks in advance.

UPDATE: The screensaver loads some image files and I was actually able to get the screensaver preview in Screensaver Preferences to show up by changing the relative file paths in my application to absolute file paths. I'm not sure why this worked. But the screensaver preview is coming up full-screen instead of scaled down inside the window like the others. I am using SDL to create a full-screen window so this probably has something to do with it. Actually the preview works like I described above but it doesn't work when Ubuntu goes into the real screensaver mode. Sorry if I'm not being clear about anything; it's sort of hard to explain what's going on.

---

### Post by the_darkside_986 on 2007-10-08
I had no idea that executables could be screensavers in gnome. I've seen it Windows though.

I think I'll program an openGL screensaver myself now.

---

