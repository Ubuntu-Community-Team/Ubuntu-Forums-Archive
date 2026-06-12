---
title: "Desktop help"
date: 2012-05-05
forum: New to Ubuntu
---

### Post by DeoHan on 2012-05-05
A week or so ago I wanted to try a new desktop theme and chose lubuntu by doing terminal: sudo apt-get install lubuntu-desktop. I also did the same for xubuntu as well. When I go to log out and sign back in and choose Ubuntu or Ubuntu 2D, I get nothing but the wallpaper for 12.04. I mean absolutely nothing. To get to the net I have to use lubuntu desktop or xubuntu desktop. My question is, how can I get Ubuntu 12.04 back the way it was and rid myself of the themes?

---

### Post by SilentMute on 2012-06-19
The first step that I would take were I you would be to remove lubuntu and xubuntu, just with sudo apt-get remove _ubuntu

this would be easiest to do within normal ubuntu, but if that's not possible you can boot in recovery mode and take them out from the recovery terminal, that should hopefully resolve the issue
--

---

### Post by Frogs Hair on 2012-06-19
After trying different desktop environments I used the method at the link successfully .
[http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu)

---

### Post by sudodus on 2012-06-19
> **DeoHan said:**
> A week or so ago I wanted to try a new desktop theme and chose lubuntu by doing terminal: sudo apt-get install lubuntu-desktop. I also did the same for xubuntu as well. When I go to log out and sign back in and choose Ubuntu or Ubuntu 2D, I get nothing but the wallpaper for 12.04. I mean absolutely nothing. To get to the net I have to use lubuntu desktop or xubuntu desktop. My question is, how can I get Ubuntu 12.04 back the way it was and rid myself of the themes?
This is strange. I made such a system maybe a couple of months ago, and it has survived through several updates without breaking Unity. I actually installed all three [klx]ubuntu-desktops to test them (for example compare speed and memory usage).

Anyway, the link to *psychocats* should help you solve your problem.

---

### Post by HiImTye on 2012-06-19
open a terminal and issue the following:
```
unity --reset
```
this should reset unity to a usable state, you will likely need to add any shortcuts you added to unity's bar again

---

