---
title: "Help :: Compiz-Fusion!!!!!!"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by zarathustra91 on 2008-06-01
Hey I installed compiz-fusion on my machine about a week ago and noticed an immediate slowdown.  (Its a laptop with an internal g-card (Intel 95x) so that was a little expected)  I thought it was because I had too many options enabled so I went through and unchecked a lot of ****.  No luck.  So then I uninstalled the manager itself (the GUI app that I used to manage what effects were on and what were off).  But now my computer is slower than ever and some features are disabled (like mulitple desktops) 

does anyone know how to solve this?  or better yet, run compiz-fusion effects without lagging out my machine?

-Zarathustra

---

### Post by philinux on 2008-06-01
System>Prefs>Appearance>Visual Effects.

Select none and see if your system comes back up to speed.

You might need to run

metacity --replace

---

### Post by zarathustra91 on 2008-06-01
thanks for the prompt response! 

I just disabled all effects and my system seems to be lagging a little less, although it still like blinks when I drag windows and my scrolling is retarded (as in slowed down) 

also, AVN just disappeared completely (I think this is because it requires something to be enabled...

what is metacity?  how do I replace it?  also... is there anything else I can do to get my system back up to speed?

[edit] 

by replace, I mean uninstall what is already installed and then install the new one.  I grasped the sudo apt-get command, so I think I know how to install it... just not uninstall(?) the other one.

---

### Post by sayakb on 2008-06-01
Setting the visual effects to none already gives you metacity.
Anyway press Alt+F2 and enter: ```
metacity --replace &
``` shall give you metacity.
For AWN dock, you need compiz to be enabled.
Also, which is your card? I have a laptop working on 945GM/GMA950 and graphics is very smooth.
The glxgears produces about 1200 FPS, but its okay for an Intel card.

---

### Post by zarathustra91 on 2008-06-01
> **LinuxIsInnovation said:**
> Setting the visual effects to none already gives you metacity.
Anyway press Alt+F2 and enter: ```
metacity --replace &
``` shall give you metacity.
For AWN dock, you need compiz to be enabled.
Also, which is your card? I have a laptop working on 945GM/GMA950 and graphics is very smooth.
The glxgears produces about 1200 FPS, but its okay for an Intel card.

I suspected I did something wrong, because I'm also running Intel 945GM on a dell inspiron e1405 laptop w/ 2GB ram and core duo @ 1.66 g.

I would really like to continue to use AWN, how would I undo the slowness of my computer and re-install compiz-fusion correctly??

p.s. I executed that code in terminal and it just did the same thing as what I did before.... same results too.  (still slow)

---

### Post by zarathustra91 on 2008-06-01
bump 

fixed the problem: hope it helps you too! 

opens synaptic package manager (system >> admin >> synaptic package...) and search for xserver-xgl... if it is installed (for me it was) uninstall / remove it. 

reboot and compiz should run smoothly!

---

