---
title: "Ubuntu 11.04 only works in classic (no effects) mode"
date: 2011-09-11
forum: New to Ubuntu
---

### Post by uf20wop on 2011-09-11
i have the same issue... here is my output

greg@Woptop:~$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
greg@Woptop:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4200 Series
OpenGL version string:  3.3.10665 Compatibility Profile Context

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

Unity supported:          yes


seems like it should be good to go, but unity never works, nor can i use anything except classic (no effects).

if i try using anything else, after i logon it makes the logon noise, and then it will just hang there without showing my desktop

---

### Post by wildmanne39 on 2011-09-11
Hi, post the results of this command please:
```
lsmod
```

---

### Post by coffeecat on 2011-09-11
@uf20wop, I've split your post out from the thread you originally posted in:

[http://ubuntuforums.org/showthread.php?t=1842094](http://ubuntuforums.org/showthread.php?t=1842094)

Together with wildmanne39's response (thanks, wildmanne39 :)).

The OP of the other thread is still active and it is very confusing dealing with more than one person's problem at the same time, even when they are similar. Generally speaking, it is better to start your own thread.

I will say that I have the same Radeon HD4200 graphics in a laptop and I can get Unity with it and the open source driver in 11.04, so hopefully this can be sorted out.

---

### Post by ddarsow on 2011-09-19
> **coffeecat said:**
> @uf20wop, I've split your post out from the thread you originally posted in:

[http://ubuntuforums.org/showthread.php?t=1842094](http://ubuntuforums.org/showthread.php?t=1842094)

Together with wildmanne39's response (thanks, wildmanne39 :)).

The OP of the other thread is still active and it is very confusing dealing with more than one person's problem at the same time, even when they are similar. Generally speaking, it is better to start your own thread.

I will say that I have the same Radeon HD4200 graphics in a laptop and I can get Unity with it and the open source driver in 11.04, so hopefully this can be sorted out.

So coffeecat, what (hoping you can recall) did you have to do to get Unity working on your machine? I am also having the exact problem on one of my personal laptops as well as on a few client computers with the Radeon HD4200 graphics.

---

### Post by anewguy on 2011-09-19
+1 - I have a MSI motherboard with built-in 4200 graphics.  If I use the restricted driver I can run Unity, but any other special effects (such as selecting classic with effects) "goes wacky!".  Well, at least some things don't work quite right - like vertical and horizontal sizes of the screen, the cube, etc..

so, I don't mean to interrupt a thread, but since it is the same adapter with a similar problem I thought I'd at least put in my 2-cents worth.

Thanks, and sorry if I've interrupted!

Dave ;)

---

