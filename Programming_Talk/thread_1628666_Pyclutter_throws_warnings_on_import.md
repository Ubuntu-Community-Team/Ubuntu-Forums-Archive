---
title: "Pyclutter throws warnings on import"
date: 2010-11-22
forum: Programming Talk
---

### Post by jakobcreutzfeldt on 2010-11-22
Hi everyone. I'm not sure if this is a good place to post it but I'll give it a shot. 

I recently acquired an old Dell Latitude D520 and I installed Maverick on it. I have python-clutter installed from the repositories. When I try to import clutter in Python, I get this:
```
** Message: pygobject_register_sinkfunc is deprecated (ClutterActor)
** Message: pygobject_register_sinkfunc is deprecated (ClutterAlpha)
** Message: pygobject_register_sinkfunc is deprecated (ClutterPath)
** Message: pygobject_register_sinkfunc is deprecated (ClutterInterval)

```Some code I've previously written breaks as a result of this, in particular, any sort of animation. 
I had Lucid installed on a Latitude D620, which, hardware-wise, doesn't seem terribly different than the D520 (faster processor, different form factor, but same graphics card (Intel 945GM), for example). The pyclutter install was fine on that computer and my code worked without problems. I switched computers and upgraded Ubuntu and now the code doesn't work. I'm not sure whether the different computer or the new OS version is to blame.

Naturally, I Googled it. I found this bug on Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/pyclutter/+bug/620499](https://bugs.launchpad.net/ubuntu/+source/pyclutter/+bug/620499)
which describes my situation exactly. When I run the small bit of code he listed, I also get a seg fault. However, the original bug reporter claims that the bug was fixed in python-clutter 1.0.2-1.0. This is the version I have but I still have the problem.

Other Google results hint that this error has shown up in other contexts so I'm not sure that it's a bug (I contributed to the above bug report anyway) but rather it's some configuration problem. I couldn't glean any solution from these other cases though.

Does anyone have any idea of what might be wrong?

btw, some software versions that I'm using (all from the Maverick repositories):
python-clutter 1.0.2-1.0
libclutter 1.2.12-0ubuntu13
python-gobject 2.21.5-0ubuntu3
python-gtk2 2.21.0-0ubuntu1
python 2.6.6

Thanks for your help!

---

