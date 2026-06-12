---
title: "X11 XGetGeometry"
date: 2012-08-26
forum: Programming Talk
---

### Post by dosh on 2012-08-26
Should XGetGeometry return the client location (x,y) of the window or the location of the whole window including the border and title bar? I'm trying to get the client position and keep get a location with XGetGeometry of 0,0 no matter where the window is positioned.

---

### Post by t1497f35 on 2012-08-27
I don't know but.
X is gonna be replaced by Wayland in the next few years (2014-2016), so writing X specific code is not welcome.
You should use the info from GtkWindow's event handlers for window resize and [move]("http://ubuntuforums.org/showthread.php?t=191866"), the Gtk move/resize event will probably be more accurate (than X's solution) because besides X the Compositor also makes decisions and sometimes it's the Compositor who makes the final decision where the window appears.

---

### Post by trent.josephsen on 2012-08-27
> **t1497f35 said:**
> I don't know but.
X is gonna be replaced by Wayland in the next few years (2014-2016)

Wow, you're optimistic. Care to place a bet? ;)

---

### Post by t1497f35 on 2012-08-27
> **trent.josephsen said:**
> Wow, you're optimistic. Care to place a bet? ;)
Not really, mostly because that's off-topic, but Mark shared even [more optimistic views]("http://www.markshuttleworth.com/archives/551") (around 2014), so my view is actually pretty realistic, and I don't mean that no one will be using X, after all there are still people proud of using OS/2.

---

### Post by cw2008can on 2013-02-12
Here is what is happening with XGetGeometry.
Ubuntu and KDE window managers create two windows
when a window is mapped. It creates a parent window,
and a parent of the parent (grandparent).
The parent of the grandparent will be the root window.

XGetGeometry of the window you created, the returned values will be:
x = 0
y = 0
width = width specified when created
height = height specified when created

XGetGeometry of the parent window, the returned values will be:
x = horizontal offset from the left side of the decoration
y = vertical offset from the top of the decoration
width = same width as specified when created
height = same height as specified when created

XGetGeometry of the grandparent window, the returned values will be:
x = horizontal location of the decoration window relative to the root window
y = vertical location of the decoration window relative to the root window
width = overall width of the window including the decoration
height = overall height of the window including the decoration

XQueryTree can be used to get the window number of the parent

Most programs do the XGetGeometry when they get the ReparentNotify event.
I found that the information was not always correct at that time,
even though it gave a successful return.
The information always seems to be correct if done at the time 
of the MapNotify event.

CW

---

