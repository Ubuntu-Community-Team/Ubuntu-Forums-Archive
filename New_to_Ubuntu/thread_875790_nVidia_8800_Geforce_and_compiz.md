---
title: "nVidia 8800 Geforce and compiz"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by fonger on 2008-07-31
Hi folks:

This is about the fifth time I'm trying to make the switchover to Linux, and before giving up, I figure I'll ask some helpful people. So I'm not a complete idiot, but am awfully close to being a moron. 

Basically, everything's working fine this time so far - except for compiz. Now, I don't have any particular use of compiz, but considering this is a new desktop, I'd like it to work. Whenever I run compiz, I get this:

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0611 (rev a2) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
*** glibc detected *** /usr/bin/compiz.real: double free or corruption (!prev): 0x08163eb8 ***

```Also, it locks up X-server and I have to reboot. (In fact, I'm typing this right now and copying and pasting it into Firefox which, I hope, still works). I've installed the proprietary nVidia drivers, but that doesn't seem to have fixed t 

I notice there was an updated driver in the nVidia website, and though it's been downloaded, I can't install it because a) it won't run unless I turn off X-server, and b) when I kill X-server (init 1), it kills my internet connection and I don't know how to restart eth01 from shell. 

All help would be much appreciate.Thank you.

---

### Post by Frenske on 2008-07-31
Did you install the compiz manager? It is a bit of long shot since I away of my Ubuntu machine!

---

