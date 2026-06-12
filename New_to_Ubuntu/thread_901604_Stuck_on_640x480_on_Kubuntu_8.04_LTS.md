---
title: "Stuck on 640x480 on Kubuntu 8.04 LTS"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by Racecar56 on 2008-08-26
Help! I'm stuck on 640x480 on my laptop after I installed the nVIDIA GeForce 7 series laptop and restarted the X server. It looks crazy! Should I restart X server again? Thanks!

EDIT: More details...
I tried the resolution thing, it won't move!
EDIT 2: Restarting X server dosen't help, I am also being annoyed of touchpad tap-to-click.
EDIT 3: Solved,thanks gjoelee!

---

### Post by super.rad on 2008-08-26
open a terminal (konsole on kde) and type sudo dpkg-reconfigure xserver-xorg and select the resolution you want then restart X by pressing ctrl+alt+bkspace

---

### Post by Racecar56 on 2008-08-26
> **super.rad said:**
> open a terminal (konsole on kde) and type sudo dpkg-reconfigure xserver-xorg and select the resolution you want then restart X by pressing ctrl+alt+bkspace

It asks about keyboard stuff, nothing about resolution.

---

### Post by gjoellee on 2008-08-26
[http://www.kshoster.net/?c=tipsandtricks&h=xfix](http://www.kshoster.net/?c=tipsandtricks&h=xfix)

---

### Post by super.rad on 2008-08-26
> **Racecar56 said:**
> It asks about keyboard stuff, nothing about resolution.

Theres questions about the keyboard, then mouse, then finally about graphics driver/resolution etc

---

### Post by Racecar56 on 2008-08-26
Like... run it again after it asks about the keyboard?

---

### Post by Wiebelhaus on 2008-08-26
Edit your applications menu to show "Screens & Graphics" then use it.

---

### Post by nonpc on 2008-08-26
Did you try installing nvidia drivers? :)

---

### Post by Racecar56 on 2008-08-26
> **nonpc said:**
> Did you try installing nvidia drivers? :)

That made the problem in the first place.

---

### Post by Otdrummer on 2009-03-07
Thank you so much!! i had a different problem where the xorg driver was malfunctioning( i have an ati radeon hd 2400 pro) and my resolution was stuck after i changed it and this completely fixed it.the driver is working fine now, media players have stopped flickering and i can use compiz properly!! thanks :)

---

