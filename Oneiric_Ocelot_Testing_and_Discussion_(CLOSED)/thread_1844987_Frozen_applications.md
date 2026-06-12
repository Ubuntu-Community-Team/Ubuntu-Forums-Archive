---
title: "Frozen applications"
date: 2011-09-16
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by DustinCasler on 2011-09-16
I'm running the beta and am having problems with applications that are minimized not reopening when clicked and also sometimes when open on the desktop the window controls are unusable. The window will be frozen on the desktop and completely unresponsive to window controls or trying to scroll, click, anything on the application. Is anyone else having this issue?

---

### Post by dino99 on 2011-09-16
seems that metacity have crashed, reload it.

---

### Post by lucazade on 2011-09-16
> **DustinCasler said:**
> I'm running the beta and am having problems with applications that are minimized not reopening when clicked and also sometimes when open on the desktop the window controls are unusable. The window will be frozen on the desktop and completely unresponsive to window controls or trying to scroll, click, anything on the application. Is anyone else having this issue?

get the same but only using unity-3d (unity-2d works well).. only workaround i've found is to switch between apps with alt+tab, then apps become responsive.

---

### Post by DustinCasler on 2011-09-16
Well, this has been happening for a few days now. I've tried reinstalling with the current daily build, restarting, downgrading to the Nvidia driver 173, but it still keeps happening without fail as I use my machine.

---

### Post by DustinCasler on 2011-09-16
> **lucazade said:**
> get the same but only using unity-3d (unity-2d works well).. only workaround i've found is to switch between apps with alt+tab, then apps become responsive.

Thanks. I haven't tried Unity 2D yet. I'll give it a try, but would ideally like to keep using 3D.

---

### Post by lucazade on 2011-09-16
> **DustinCasler said:**
> Thanks. I haven't tried Unity 2D yet. I'll give it a try, but would ideally like to keep using 3D.

of course :)
just pointing out that the bug could be related to compiz because not used in unity-2d.

---

### Post by DustinCasler on 2011-09-16
> **lucazade said:**
> of course :)
just pointing out that the bug could be related to compiz because not used in unity-2d.

Well, you mmight have been right. I've been in Unity 2D since right after my last post and so far i'm unable to recreate the error. I've tried opening up everything that gave me trouble in 3D and minimizing and stuff to see if it would freeze or refuse to reopen. But so far everything's working as it should. But i've only used it for a few minutes. I'll try it again tomorrow and report if the issues show up in 2D.

---

### Post by lucazade on 2011-09-16
> **DustinCasler said:**
> Well, you mmight have been right. I've been in Unity 2D since right after my last post and so far i'm unable to recreate the error. I've tried opening up everything that gave me trouble in 3D and minimizing and stuff to see if it would freeze or refuse to reopen. But so far everything's working as it should. But i've only used it for a few minutes. I'll try it again tomorrow and report if the issues show up in 2D.

ok, good to know.

another trial to see if it is really compiz the problem and to be sure to open a proper bug report, is to try to replace the window manager in a unity-2d session by using:
compiz --replace
this will switch from metacity to compiz inside unity-2d, just temporary, then check if bug is present

---

### Post by mc4man on 2011-09-16
Could be your install has gotten a bit borked, seen that here several times over the course of the dev. I'll probably dump my beta 1 this weekend for a fresh start
Anyway there are a few things that can go wrong currently when minimizing windows
This bug is being fixed - have suggested a workaround in the report till then - 
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/847967](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/847967)

This issue, maybe i'm the only one that has it, - it causes a launcher icon to not restore a minimized window
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/838055](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/838055)

---

### Post by DustinCasler on 2011-09-16
> **mc4man said:**
> Could be your install has gotten a bit borked, seen that here several times over the course of the dev. I'll probably dump my beta 1 this weekend for a fresh start
Anyway there are a few things that can go wrong currently when minimizing windows
This bug is being fixed - have suggested a workaround in the report till then - 
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/847967](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/847967)

This issue, maybe i'm the only one that has it, - it causes a launcher icon to not restore a minimized window
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/838055](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/838055)

Thanks for the links. I definitely have the second one also. I know it's not a borked install, that was my first idea. So I tried a fresh install from both the official Beta 1 disc as well as the current daily. And I never fail to get these issues almost immediately. I used Unity 2D for about an hour last night and i've been on it for about an hour so far today and so far i've yet to see any of the problems. So i'm thinking at least on my machine it has to be a compiz related issue.

---

### Post by philinux on 2011-09-16
Ditto all the above. 64 bit nVidia active. Me thinks its a compiz/unity plugin buglet.

---

### Post by mc4man on 2011-09-16
> **DustinCasler said:**
> Thanks for the links. I definitely have the second one also. I know it's not a borked install, that was my first idea. So I tried a fresh install from both the official Beta 1 disc as well as the current daily. And I never fail to get these issues almost immediately. I used Unity 2D for about an hour last night and i've been on it for about an hour so far today and so far i've yet to see any of the problems. So i'm thinking at least on my machine it has to be a compiz related issue.

Those 2 issues are unity-3d only. The 1st. one should be fixed in the near future. 
The 2nd one remains unconfirmed though maybe it's a known bug elsewhere, sometimes searching LP bugs can prove less than fruitful.
(though good to hear it's not only me on that one.

---

