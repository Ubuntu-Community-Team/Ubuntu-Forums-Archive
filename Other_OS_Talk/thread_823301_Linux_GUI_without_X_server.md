---
title: "Linux GUI without X server?"
date: 2008-06-09
forum: Other OS Talk
---

### Post by babylon2233 on 2008-06-09
Is there any other way to implement GUI without using X11? Take a look on Mac OS X GUI. I believe we can also do the same with Linux. Don't talk about downside of this approach here. I just want to know if there is any project trying to implement this kind of GUI.

---

### Post by regomodo on 2008-06-09
I believe the term is framebuffer

[http://en.wikipedia.org/wiki/Linux_framebuffer](http://en.wikipedia.org/wiki/Linux_framebuffer)

---

### Post by ingvildr on 2008-06-09
Doesn't Mac just use some forked version of XFree86?

---

### Post by babylon2233 on 2008-06-09
> **ingvildr said:**
> Doesn't Mac just use some forked version of XFree86?

No, mac use X server only to run existing X11 apps(X.org not XFree86).Mac OS X not using X Server for its GUI.

---

### Post by ingvildr on 2008-06-09
What is it exactly that Mac does that you want on Linux, because i had a little read up and OSX uses Quartz which is itself a window server like X11.

If your talking about the compositing (Quartz Compositor/Extreme) Linux has that in the form of Compiz/Metacity/Kwin/Xfwm plus AIGLX/XGL or if your talking about the actual widgets provided by Cocoa then no :), we already have QT4 and GTK2 the former which now has full svg theming capability so hopefully some exciting things will come from that :)

---

### Post by babylon2233 on 2008-06-09
OK,So, Why it seems Mac OS X GUI system superior to Linux GUI?

---

### Post by ingvildr on 2008-06-09
In what way?

---

### Post by SunnyRabbiera on 2008-06-09
> **babylon2233 said:**
> OK,So, Why it seems Mac OS X GUI system superior to Linux GUI?

In what way?
I think the linux GUI is better as most of it is customizable, OSX is stuck with aqua unless you use third party software.

---

### Post by babylon2233 on 2008-06-09
because based on what i understand, Mac OS X core, Darwin or XNU is worse than Linux and what make Mac OS X so popular is its top layer above the core os. So, it seems there is something special about it.

Sorry for my bad english:)

---

### Post by SunnyRabbiera on 2008-06-09
Yes but linux GUI cores are no different in the end as both OSX and linux are based on a unix like core.

---

### Post by 3rdalbum on 2008-06-09
> **babylon2233 said:**
> because based on what i understand, Mac OS X core, Darwin or XNU is worse than Linux and what make Mac OS X so popular is its top layer above the core os. So, it seems there is something special about it.

Mac OS X is popular because Apple promotes a lifestyle image.

We could re-create an exact replica of the Mac OS X GUI on top of X, down to the last detail. Some people already get pretty close with Gnome.

I don't think you understand what the X server is. It's just a program that sends video data to the monitor, accepts input from the mouse, draws an arrow on the screen and allows applications higher up to allocate rectangles to draw into. That's a simplification, but X11 infamously provides "process, not policy". That is, X just handles the drawing of objects. It's up to programs to decide what the objects should look like.

The Quartz system of OS X is the exact equivilant of X - they do the same thing. If Apple wanted to, they could rip out Quartz and replace it with an X11-based server, and nobody would notice. Maybe they already do it? The difference between Quartz and X is that Quartz uses Display Postscript as its internal language, and Xorg uses X11 objects as its internal language. The advantage of Quartz is that you can create PDFs of regions on-screen. The advantage of X11 is that you can run GUI programs across a network. I know which one I prefer :-)

---

### Post by babylon2233 on 2008-06-09
I'm already stop talking about GUI actually after I realize Quartz is a window server. But what I mean with the top layer is Core services and other APIs provide by Apple with their OS. I know what X11 is, I just don't know what Quartz is and how Mac OS X GUI works. Anyway, thanks for your info.

---

