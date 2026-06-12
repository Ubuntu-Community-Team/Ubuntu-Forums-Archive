---
title: "Unity 3d effects"
date: 2011-12-27
forum: New to Ubuntu
---

### Post by sideffects on 2011-12-27
Okay, so I feel like a loser, but I've been out of the Ubuntu loop since 9.10. I'm kinda liking the looks of Unity, but I am having a hard time trying to figure out 3d effects. In 9.10 I was using Compiz. I have CCSM installed on 11.10, but with no results. I read something on a blog that Unity uses Mutter for 3d effects, but I'm lost as to what they are talking about. Any help would be greatly appreciated.

---

### Post by wildmanne39 on 2011-12-27
Hi, unity uses compiz unless you are using gnome and not unity.

What version of ubuntu are you using? and please post the results of these two commands.
```
/usr/lib/nux/unity_support_test -p
```
```
lspci | grep VGA
```
Thanks

---

### Post by sideffects on 2011-12-27
> **wildmanne39 said:**
> Hi, unity uses compiz unless you are using gnome and not unity.

What version of ubuntu are you using? and please post the results of these two commands.
```
/usr/lib/nux/unity_support_test -p
```
```
lspci | grep VGA
```
Thanks

```
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
OpenGL version string:  2.1 Mesa 7.11

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```

```
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
```

---

### Post by wildmanne39 on 2011-12-27
Hi, click on the second link in my signature and that is a guide for setting up compiz in several versions of ubuntu so please read the whole page carefully and make sure you are following the directions for 11.10 and if you have any problems there are links to revert unity or compiz if needed.
Thanks

---

### Post by sideffects on 2011-12-27
Thanks! I will let you know how it goes

---

