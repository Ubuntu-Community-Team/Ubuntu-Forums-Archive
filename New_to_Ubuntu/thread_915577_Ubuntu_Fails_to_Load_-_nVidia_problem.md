---
title: "Ubuntu Fails to Load - nVidia problem"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by jon_fairley on 2008-09-10
My name is Jon Fairley and I am new to Linux and have a problem.

I went to increase my appearance settings, and followed on screen instructions to download a driver for my nVidia graphics card. All seemed to go well until I restarted my PC. The Ubuntu load screen shows, but once the OS attempted to load, my screen glitches and looks like 'snow' on a TV set. 

I am unable to do anything at this point and have been forced to reboot into my Windows partition (I am dual booting) as Ubuntu will not load.

I had no problems with it until I updated my graphics driver and restarted. 

Any help is appreciated. Thanks.

---

### Post by Zzl1xndd on 2008-09-10
In your boot menu there should be a safe graphics mode, give that a try.

---

### Post by panhandle on 2008-09-10
First:

[http://ph.ubuntuforums.com/showthread.php?t=797270](http://ph.ubuntuforums.com/showthread.php?t=797270)

Also...you are not alone.

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/231989](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/231989)

When you finally have access to your desktop, consider the following link for stable video until you get your nVidia problems sorted (note that this is archived from Gutsy):

[http://ubuntuforums.org/showthread.php?t=399630](http://ubuntuforums.org/showthread.php?t=399630)

---

### Post by skippuff54 on 2008-09-10
1. mess with your refresh rate settings, as well as ur screen resolution. TV screens refresh at different rates than computer monitors, and u might need to adjust the rate so the tv can pick up the signal (or so the CPU can handle the vid card properly without crashing...i dunno exactly what happens but messin with the refresh rate worked for me)

2. make sure u got the proper nVidia drivers for ur card and ur Ubuntu distro. make sure they r right for gnome (ubuntu), kde (kubuntu)or xfce (xubuntu)

---

