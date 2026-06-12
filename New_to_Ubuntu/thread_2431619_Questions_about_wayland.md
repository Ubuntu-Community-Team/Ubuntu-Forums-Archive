---
title: "Questions about wayland"
date: 2019-11-19
forum: New to Ubuntu
---

### Post by hk42 on 2019-11-19
On my 19.04 installation I have the option to choose "Ubuntu on wayland"
when login.
I see no difference  so my questions are:
How to know on a running GUI if it is using wayland ?
What are the applications where I could notice a difference ?
I installed other windows managers (XFCE and KDE) they work great
but there is no option when choosing them. Why ?

---

### Post by crip720 on 2019-11-19
Wayland like Xorg run behind the scenes.  They are the programs that make your screen work, not the nice picture that programs/desktops like Grome, XFCE or KDE put on.  Wayland is new and is suppose to replace Xorg, which is old and bloated.  Wayland can have some bugs still in it.  
If you have installed XFCE and or KDE desktops to your system, you should be able to select them the same way as you select Wayland, they should be on that screen as extra options.  Adding more desktops can mess up your desktop and/or system, depending on which desktops you add, some work okay together, others don't.

---

### Post by TheFu on 2019-11-19
The main issues I recall with Wayland was the lack of remote window support. If you commonly work on different systems and have the window displayed locally, this is full-stop problem and a reason never to use wayland.

Failures of image and video capture tools to work at all was another issue reported.  If you want to record the screen, that's a pretty big deal.

I have no idea if 19.04 fixed those or not.  At this point, people should be pretty close to moving to 19.10 anyways, assuming they aren't sticking with LTS releases.

---

### Post by maglin2 on 2019-11-19
I gave up using wayland on kubuntu 18.04 because synaptic wouldn't run. Don't know if it does in 19.04.
If you have logged in to a wayland session xeyes will show if specific applications are really running natively uner wayland, or if they use xwayland.

---

### Post by hk42 on 2019-11-19
Thanks for the quick answers.
Yes synaptic doesn't run on wayland so it's a good way to remind me that I'm using it.
For selecting the various windows managers yes I have a (rather uggly) menu to
choose them it has even an entry for a full screen kodi.
I used apt to install them and GUI installation programs were updated nicely.

---

