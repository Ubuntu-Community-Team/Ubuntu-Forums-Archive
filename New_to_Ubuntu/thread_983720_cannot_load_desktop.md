---
title: "cannot load desktop"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by Shadowmeph on 2008-11-16
I cannot log into Kubuntu I get to the sign in page and when I put my password in and try to boot to my desktop I get

> X session: unable to start X session---no " /home/shadowfire/.xsession" file no session managers, no windows managers and no terminal emulators found. aborting
I cannot do anything. I tried fail safe and I get the simalar message saying " unable to launch failsafe.
if anyone knows how to fix this please tell me so I can.

---

### Post by empthollow on 2008-11-16
if you press ctrl + alt + F2 you can log in to a terminal.  I would do some investigating to see if that file exists and what is in it.  there is no such file in my home directory but i am using gnome.

---

### Post by Keen101 on 2008-11-16
wow. I'm not at all sure if this will help, but here goes anyway.

It looks like most of your files have either been removed by a bad upgrade, or a failed install.

Try going to the recovery mode when booting into GRUB, and get to a terminal. Put this in your terminal: 

```
sudo apt-get install Kubuntu-desktop

```
hopefully that will install everything you need.

---

### Post by boblemur on 2008-11-16
thats strange because i dont have a .xsession file and i have no problems

however i dono why it dosent find ur desktop :S

---

### Post by Shadowmeph on 2008-11-16
> **Keen101 said:**
> wow. I'm not at all sure if this will help, but here goes anyway.

It looks like most of your files have either been removed by a bad upgrade, or a failed install.

Try going to the recovery mode when booting into GRUB, and get to a terminal. Put this in your terminal: 

```
sudo apt-get install Kubuntu-desktop

```
hopefully that will install everything you need.

I just tried this and I still get the same

---

### Post by boblemur on 2008-11-16
Try the ctrl + alt + f2 thing and then login and run ```
startx
``` see what happens.

you could try...

```
sudo apt-get install --reinstall Kubuntu-desktop
```

hope this works...

---

### Post by Shadowmeph on 2008-11-16
> **boblemur said:**
> Try the ctrl + alt + f2 thing and then login and run ```
startx
``` see what happens.

you could try...

```
sudo apt-get install --reinstall Kubuntu-desktop
```

hope this works...

nope neither worked

---

### Post by Shadowmeph on 2008-11-16
Darn I guess I will try a different distro

---

### Post by boblemur on 2008-11-17
Does this happen on the kubuntu live cd???

if so try the normal ubuntu one or the xubuntu one

---

