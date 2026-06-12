---
title: "Dual Monitor Programming"
date: 2011-09-18
forum: Programming Talk
---

### Post by N1GHTS on 2011-09-18
There is a situation in which I need two programs I wrote in C to run full screen on two separate monitors using Ubuntu Server with a basic Xorg installation (no window manager). When Xorg launches, it needs to automatically execute and place one program in one screen, the other in the other.

Here is what I need some help configuring:

1. How do I tell a basic configuration of Xorg that there are two monitors? Both of these monitors have different screen resolutions.

2. I know how to launch a program automatically with Xorg's launch (xinitrc), and I think launching more than one requires that I put an ampersand after the first program command line in xinitrc, but how do I program the second program not to overlap the first one and instead appear on the second monitor? I am only using the SDL and OpenGL libraries for drawing the interface.

---

### Post by karlson on 2011-09-18
> **N1GHTS said:**
> There is a situation in which I need two programs I wrote in C to run full screen on two separate monitors using Ubuntu Server with a basic Xorg installation (no window manager). When Xorg launches, it needs to automatically execute and place one program in one screen, the other in the other.

Here is what I need some help configuring:

1. How do I tell a basic configuration of Xorg that there are two monitors? Both of these monitors have different screen resolutions.

2. I know how to launch a program automatically with Xorg's launch (xinitrc), and I think launching more than one requires that I put an ampersand after the first program command line in xinitrc, but how do I program the second program not to overlap the first one and instead appear on the second monitor? I am only using the SDL and OpenGL libraries for drawing the interface.

1.  /etc/X11/xorg.conf or I think there is a way to get access to the size of the screen although I don't remember what it is in Xlib.

2.  Why do you want to launch at Xinit time?  Or do you not want to have the users have any window manager whatsoever?  If you need to make X program appear on 1st monitor and 2nd on the 2nd you should just give it the appropriate X and Y coordinates at launch.

I still think that you are making it more complicated then it needs to be.

---

### Post by N1GHTS on 2011-09-18
Karlson, Thank you for your response. For some reason I couldn't put 2 and 2 together on that subject, but your response triggered the right connections in my brain and now I know generally how to make it work.

For xorg.conf, i'll read the [man page]("http://www.x.org/archive/X11R6.8.1/doc/xorg.conf.5.html") for it since I'm sure its obvious how to do it.

For the window positioning, I can use the [SDL_SetVideoMode]("http://sdl.beuc.net/sdl.wiki/SDL_SetVideoMode") function.

As always, thanks for your help.

---

