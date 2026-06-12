---
title: "nvidia question about blacklist"
date: 2011-10-17
forum: New to Ubuntu
---

### Post by critin on 2011-10-17
I ran the test and this is the result.

```
  crit@crit-Dimension-4550:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce FX 5200/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 173.14.30

Not software rendered:    yes
Not blacklisted:          no
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no
crit@crit-Dimension-4550:~$ 

        
```Can it be taken off the Blacklist and work?  I am running 2D and it seems to work fine.
I did install the updated driver

Thanks, critin

---

### Post by gsmanners on 2011-10-17
That card is mighty old. You really think it can handle Unity?

---

### Post by critin on 2011-10-17
I don't know, thats why I'm asking.  lol  I couldn't run Unity in 11.04 (pop-up said: This machine cannot run Unity)  so I chose gnome classic.  On 11.10 it didn't alert me that Unity couldn't run so I didn't have to choose anything.  Nothing stalled or froze and the screen looks like Unity to me.  It works great. 

I logged out and back in to a 2D session to check it out.  It looks the same as the original install desktop. 3D or 2D?  How can I tell which I'm running in the original session?

Just curious about blacklists.  Thanks.

critin

---

