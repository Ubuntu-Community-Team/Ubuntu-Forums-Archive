---
title: "Compleley new Linux GUI system"
date: 2012-11-25
forum: Programming Talk
---

### Post by vanangamudi on 2012-11-25
If I could spent a year or two for developing completely new GUI system without any dependency on X-windowing system, what would be the way. Does Mesa OpenGL library depend upon GLX??  I have heard about new Wayland compositor for OpenGL ES. but it is for OpenGL ES. what about complete OpenGL. the Goals of Wayland seems to be much more intuitive. So I'm thinking of doing it for complete OpenGL library. Hardware accelerated Windowing system is the future in desktops atleast. Can anybody tell us or guide us to completely eliminate X from Linux. I'm not that against X.  but there are lot of dependencies for GLX. 

simply, If I want to write completely new Windowing system, is it possible to count on Mesa or the binary video driver from vendors and the default drivers for input devices???

---

### Post by trent.josephsen on 2012-11-25
What is your current level of knowledge?

If your goal is to move Linux away from X (which I fully support), your abilities would probably do their best service advancing Wayland. Test it, debug it, write patches and do your best to make it happen as soon as possible. Creating a new windowing system would just increase fragmentation IMO.

As for Wayland using GLES, the reason for that is in the [FAQ](http://wayland.freedesktop.org/faq.html#heading_toc_j_12):

>  EGL is the only GL binding API that lets us avoid dependencies on existing window systems, in particular X. GLX obviously pulls in X dependencies and only lets us set up GL on X drawables. The alternative is to write a Wayland specific GL binding API, say, WaylandGL.

A more subtle point is that libGL.so includes the GLX symbols, so linking to that library will pull in all the X dependencies. **This means that we can't link to full GL without pulling in the client side of X, so we're using GLES2 for now. Longer term, we'll need a way to use full GL under Wayland.** [emphasis mine]
Bottom line, GL and X are currently too closely bound to easily separate. That last sentence sounds like a challenge to me, though, so that might be a good place for you to start.

---

### Post by vanangamudi on 2012-11-26
is there any layout picture of inter dependency of the following components??.. with enough description

DDX
X-server
GLX
Xvesa
Mesa/Opengl
DRI
DRM
Wayland
User apps
and the others (please include the other components if any)


[SIZE=3][IMG]http://3.bp.blogspot.com/-yp99PzEORDI/T1no3lrZlCI/AAAAAAAAABI/RV7ODuT6qlw/s1600/EGL-Mesa-Wayland-arch.png[/IMG][/SIZE]

this explains clearly how wayland is independent of X-server. can any one make a picture like this... so that we can understand how the linux graphics stack is working.

---

