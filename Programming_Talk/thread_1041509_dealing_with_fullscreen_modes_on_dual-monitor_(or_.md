---
title: "dealing with fullscreen modes on dual-monitor (or more) systems"
date: 2009-01-16
forum: Programming Talk
---

### Post by jyaan on 2009-01-16
I have been wondering for some time now how to dual-monitor-proof fullscreen mode. Writing OpenGL and SDL code results in a fullscreen app that stretches across both screens, giving a small area of the dimensions specified (for the fullscreen resolution) with the remained filled in black.

How can I make an application fullscreen to the primary display (only)? Is it possible with SDL, or is this functionality not yet implemented? In Warsow, the configuration file allows for display selection. Nexuiz also appears to work properly. Even Half-Life 2 in Wine works correctly after some tweaking, while certain games like X-Moto do not. How can I code this functionality? Some links to documentation/examples would be nice.

Thanks in advance.

---

### Post by jyaan on 2009-01-16
I just tried out JOGL, and Java exclusive mode appears to support what I want. Of course, I'm not really a Java programmer, but I _am_ interested in it. I'm thinking for C/C++ I might have to drop SDL for windowing for now and use GLX or similar. That is a bit of a pain, however, since I'll have to write separate windowing backends for each OS. :(

---

