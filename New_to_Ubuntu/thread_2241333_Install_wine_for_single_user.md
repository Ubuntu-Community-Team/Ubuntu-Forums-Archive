---
title: "Install wine for single user"
date: 2014-08-25
forum: New to Ubuntu
---

### Post by anchitsingh9 on 2014-08-25
I want to run some windows based programs using wine.
The thing is that I do not want to install wine systemwide.
I know that the maximum damage wine can cause is only to /home folder, but still I would prefer full control.
So is there a way that I can compile the source and restrict the installation for single user (Standard user) ?
Also where could I find the stable 1.6.2 source..?

---

### Post by sotiris2 on 2014-08-25
Well you could install wine normally and change the executable's group to yours and change permissions so that other users won't be allowed to run it. 
As in the following```
sudo chown root:user `which wine`; sudo chmod o-x `which wine`
```
Replace user with a group you are in and the other users are not. (you are in a group which is same as your username, so most likely candidate). To check do ```
groups
```

---

### Post by Mark Phelps on 2014-08-25
> I want to run some windows based programs using wine.Wine is not an emulator that runs lots of Windows programs, instead, it is a "hack" that only runs SOME programs.

Before you put a lot of effort into installing and customizing Wine, visit the WineHQ website and look up the compatibility ratings of the windows programs and versions you want to run.

Anything not found, or rated less than Gold, is wasting your time installing Wine.

---

### Post by anchitsingh9 on 2014-08-26
Thanks to both of you.
I'll see what I should do.

---

