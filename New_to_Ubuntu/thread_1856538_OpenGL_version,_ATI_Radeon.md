---
title: "OpenGL version, ATI Radeon"
date: 2011-10-08
forum: New to Ubuntu
---

### Post by TheMacyp on 2011-10-08
Hello there!
I'm new to the forums, and I have some questions regarding OpenGL in Ubuntu.
I've installed Ubuntu 11.04 a week ago and never messed with the graphics drivers, so I guess I'm using the Open-source ones, even though I'm not sure.
My graphics card is an ATI Radeon HD 5145 (512 MB) - 01:00.0 VGA compatible controller [0300]: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series] [1002:9553]
- and when I write (in terminal):

glxinfo | grep -i opengl 

I get:

OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on AMD RV710
OpenGL version string: 2.1 Mesa 7.10.2
OpenGL shading language version string: 1.20
OpenGL extensions:

Typing "LIBGL_DEBUG=verbose glxinfo" gives me this:

direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
...
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
...
GLX version: 1.4


Is this information correct?
Above, shouldn't it say "ATI/AMD" instead of "X.Org"? And why is it that I only have OpenGL v1.4, when my graphics card says it supports v2.0?

Thanks in advance, guys.

---

### Post by oldos2er on 2011-10-08
Post moved to its own thread. In the future, please start a new thread rather than posting in a thread more than a year old; you're much more likely to get help that way.

---

