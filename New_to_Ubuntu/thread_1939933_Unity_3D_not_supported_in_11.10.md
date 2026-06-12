---
title: "Unity 3D not supported in 11.10"
date: 2012-03-12
forum: New to Ubuntu
---

### Post by mabari99 on 2012-03-12
I have finally got the nvidia driver working without changing resolution and Gnome Classic looks great. It is interacting with CCSM and I have wobbly windows and the cube working. Love it. So, I thought, it's time to get Unity working too. So I log in with Ubuntu and get the Unity desktop which I also like. Unfortunately the wall 4 desktops thingy is not working. When I click on it, it only has 1 desktop, not 4. So I did the following in Terminal:

mabari@mabari-desktop:~$ /usr/lib/nux/unity_support_test -p
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
mabari@mabari-desktop:~$ 

I was surprised to see it say that Unity 3D is not supported since it works OK in Gnome Classic. Also, what do I need to blacklist?

Oh dear! Here I am with all these questions bugging you poor Ubuntu experts yet again. Please forgive me. And the big question:

Is there life BEFORE death?

Looking forward to an explanation from an honest expert.

Thanks

---

### Post by alphacrucis2 on 2012-03-12
Not blacklisted: no

I presume that means your card is blacklisted (double negative and all that). So you would want to un blacklist it. No idea why it would be blacklisted though.

A search found this:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/772207/comments/55](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/772207/comments/55)

---

### Post by mabari99 on 2012-03-12
Doesn't look good. From what the comment you posted said, it seems like I can only get compiz working on Classic or Unity, and even then Unity is missing the icons on the left bar.

I did follow the steps that someone else had posted to get Classic and Unity working, and at the end of that I had a hybrid desktop with the Unity left side vertical bar, but again with no icons showing, although if I hovered the mouse, it would say which icon and if I clicked, it would load the appropriate option. It also had the compiz settings with wobbly windows and the four desktops on the bottom bar with cube enabled.

But it looks like I'm sticking with Classic until someone tells me a foolproof way to get Unity enabled properly.

---

