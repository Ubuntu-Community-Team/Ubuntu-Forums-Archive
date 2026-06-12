---
title: "Forcing __GL_FSAA_MODE on the fly"
date: 2011-11-01
forum: Programming Talk
---

### Post by Sworddragon on 2011-11-01
Some weeks ago I have begun to write my first public project. It is called [xprofile](http://sourceforge.net/projects/xprofile) and is something like nHancer for Windows. If a special application like a game is active it can load user defined graphic configurations during this time.

But there is a problem: Some driver configurations like anti aliasing can be only set before the application is initializing. But xprofile is getting the active application from the window name. Even if I use the event handler from Xlib and set __GL_FSAA_MODE directly after the window is created it is already too late because the OpenGL initialization is already finished.

Maybe there is a way to force the application to use anti aliasing on the fly. For example some years ago on Windows I could change anti aliasing on the fly with the nvidia driver. But tis has changed after some time. Maybe there is a way on Linux to force the driver (in this example nvidia) to draw the objects with anti aliasing or maybe there is another hackish way to get a solution. But currently I'm out of ideas and can't develop xprofile on this way anymore.

---

