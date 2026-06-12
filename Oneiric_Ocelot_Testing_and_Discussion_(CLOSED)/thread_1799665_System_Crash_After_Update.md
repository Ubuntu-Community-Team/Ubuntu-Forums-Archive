---
title: "System Crash After Update"
date: 2011-07-07
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by PhantmKllr on 2011-07-07
I had been running Oneric alpha 1, but I decided to switch back to 11.04.

Now that alpha 2 is out, I'd like to take it for a spin; so I took my alpha 1 ISO (due to internet bandwidth constraints), copied it to a flash drive (using LinuxLive USB creator: [http://linuxliveusb.com/]("http://linuxliveusb.com/")), and installed it on my computer.

After installation, I installed Ndiswrapper for my wireless card, and ran apt-get update and upgrade. All is well.

Now, here's my problem, after restarting the computer, when the login prompt is reached, the computer freezes completely. The cursor won't move, the keyboard does nothing, and there is no indication of activity.

---

### Post by cariboo on 2011-07-08
Are you using lightdm or gdm? IF you're using lightdm, can you get to a console and restart lightdm.

---

### Post by ZekeGraal on 2011-07-08
I have this EXACT same problem, I upgraded to 11.10 alpha 2, and I chose to use lightgdm. My touchpad and keyboard don't work, BUT, for some reason I can attach an external mouse and keyboard and it will work, which is how I am typing this... Any way to revert to gdm after I've logged in?

---

### Post by vulfgar on 2011-07-09
I have a similar problem. 

I installed oneiric and then gnome-shell. A couple of days later, after updates I restarted and logged in to GS, but it crashed so I had to restart. After this the keyboard and mouse didn't work when the login-menu appeared. It works perfectly in text-mode so there is no hardware failure. I thoutht this might be a fault in lightdm so I installed gdm and changed to login via gdm, but the problem remained. If I unplug the mouse I can get it to work and if I plugin an external keyboard I can login and that work to, but I can't get the built-in keyboard to work (it's a laptop). 

The thing is I have a parallel installation of oneiric on this computer, I updated natty to oneiric after the latter repositorys opened. That old installation is rock-solid, works perfectly in both unity and GS and I've never experienced the above problem in that isntallation. The newer installation though is very instable, programs crashes all the time.

---

### Post by jeffreisch on 2011-07-10
> **vulfgar said:**
> I have a similar problem. 

I installed oneiric and then gnome-shell. A couple of days later, after updates I restarted and logged in to GS, but it crashed so I had to restart. After this the keyboard and mouse didn't work when the login-menu appeared. It works perfectly in text-mode so there is no hardware failure. I thoutht this might be a fault in lightdm so I installed gdm and changed to login via gdm, but the problem remained. If I unplug the mouse I can get it to work and if I plugin an external keyboard I can login and that work to, but I can't get the built-in keyboard to work (it's a laptop). 

The thing is I have a parallel installation of oneiric on this computer, I updated natty to oneiric after the latter repositorys opened. That old installation is rock-solid, works perfectly in both unity and GS and I've never experienced the above problem in that isntallation. The newer installation though is very instable, programs crashes all the time.




i have the same thing. now my mini-10 , is a desktop , not a netbook , as i need an external kbd and mouse

---

### Post by dino99 on 2011-07-10
maybe that will help you:

[http://ubuntuforums.org/showpost.php?p=11010319&postcount=14](http://ubuntuforums.org/showpost.php?p=11010319&postcount=14)

---

### Post by PhantmKllr on 2011-07-11
> **cariboo907 said:**
> Are you using lightdm or gdm? IF you're using lightdm, can you get to a console and restart lightdm.

At first, it was GDM, then I restarted into recovery mode, and ran "apt-get dist-upgrade", which brought me to LightDM.

I don't know how to get to a console from LightDM, but I tried "CTRL -> ALT -> F2", and that didn't work.

> **ZekeGraal said:**
> I have this EXACT same problem, I upgraded to 11.10 alpha 2, and I chose to use lightgdm. My touchpad and keyboard don't work, BUT, for some reason I can attach an external mouse and keyboard and it will work, which is how I am typing this... Any way to revert to gdm after I've logged in?

I don't think that you're having the same problem as me. I work on my laptop with an external mouse all the time. The problem I'm having is that the X-server completely freezes up, and the computer will not accept any input.

> **dino99 said:**
> maybe that will help you:

[http://ubuntuforums.org/showpost.php?p=11010319&postcount=14](http://ubuntuforums.org/showpost.php?p=11010319&postcount=14)

Checked the link, looks as if they're having a different problem than I have.

Anyways, not very much of a problem anymore, as I'm experimenting with my dekstop computer instead. (Installing 11.10a2 as I write.)

But seriously, this is a very weird problem, and I don't think it's LightDM's fault.

---

### Post by lonniehenry on 2011-07-11
I just did updates after a couple of days away and I am experiencing the same no keyboard, no mouse until I unplug it and replug it and then it then works. I am on a laptop and the keyboard fails. I will go looking for a keyboard to plug in.

---

### Post by Harry33 on 2011-07-12
> **lonniehenry said:**
> I just did updates after a couple of days away and I am experiencing the same no keyboard, no mouse until I unplug it and replug it and then it then works. I am on a laptop and the keyboard fails. I will go looking for a keyboard to plug in.

This is the original bug report (807306) about this issue:
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/807306](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/807306)
There are several duplicates also: 807291, 807538, 808599, 808890.

A good workaround is to rename the directory /run/udev
for example to /run/udev.old
or
just to remove the directory /run/udev

---

### Post by VinDSL on 2011-07-12
> **Harry33 said:**
> A good workaround is to rename the directory /run/udev
for example to /run/udev.old
I renamed mine /run/u.devil

LoL!  :D

---

### Post by lonniehenry on 2011-07-12
Thanks Harry33,  worked like a charm.

---

### Post by Harry33 on 2011-07-12
> **vindsl said:**
> i renamed mine /run/u.devil

lol!  :d

:d

---

### Post by PhantmKllr on 2011-07-12
Alright, now I feel foolish.

After updating my desktop computer to 11.10, I was experiencing the same problem.

But instead of shutting the computer down immediately, I decided to wait a little bit. After a few seconds, I was able to use the cursor. No keyboard input.

It was then that I re-plugged my keyboard and mouse, and they worked!

So, apologies to everyone, looks like I am having the same problem that you are.

I'm just going to mark the thread as solved. I've rolled back to 11.04 for the time being.

Thanks.

---

