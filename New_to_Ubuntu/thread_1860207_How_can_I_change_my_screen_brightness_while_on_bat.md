---
title: "How can I change my screen brightness while on battery permanently?"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by einov on 2011-10-14
I would like to save my battery as much as I can while I work with my laptop on battery alone. How do I change the settings so that the screen brightness is at its lowest settings whenever I use my laptop on battery?

---

### Post by collisionystm on 2011-10-14
> **einov said:**
> I would like to save my battery as much as I can while I work with my laptop on battery alone. How do I change the settings so that the screen brightness is at its lowest settings whenever I use my laptop on battery?

what version of ubuntu

---

### Post by ubudog on 2011-10-14
Search for Power Management on 11.04 and above, or go to System>Preferences>Power Management on 11.04 Classic and below.

---

### Post by collisionystm on 2011-10-14
> **ubudog said:**
> Search for Power Management on 11.04 and above, or go to System>Preferences>Power Management on 11.04 Classic and below.

except 11.10

there is no brightness applet.

---

### Post by ubudog on 2011-10-14
> **collisionystm said:**
> except 11.10

there is no brightness applet.

Oh really?  Didn't know that.  :)

---

### Post by collisionystm on 2011-10-14
> **ubudog said:**
> Oh really?  Didn't know that.  :)

Yeah its a bit annoying! I cant wait until all official features of gnome3 are finally integrated... 11.10 gnome-shell is actually pretty outdated!

---

### Post by einov on 2011-10-14
Oh sorry I forgot to mention the version I'm running. Yea I'm using 11.10. Does anyone know how to change the brightness permanently in this version?

---

### Post by einov on 2011-10-17
I hate to double post but does anyone know a solution to this problem? **Once again the problem is that the brightness setting I set up in System Settings > Screen does not get saved for some reason. Every time I restart my laptop, the screen is on its brightest setting!**

---

### Post by sid1907 on 2011-10-17
I got the same problem on 11.10.

Any help? Anyone!!?

---

### Post by owiknowi on 2011-10-18
don't know if this still works, but it did untill v.10.10

go to the file : /etc/rc.local
open it as root / administrator (or use in a terminal: yourname@computername:~$ sudo edit /etc/rc.local

and add the following line (value 2 can also be 1 depending on the screen, f4 can be another key too on your keyboard (use that) and 20 stands for 20% brightness, which is not a whole lot ;) ):

setpci -s 00:02.0 F4.B=20

p.s. this will become the default value for your screen, both on ac or on battery.

hope this still works!

---

### Post by einov on 2011-10-19
> **owiknowi said:**
> don't know if this still works, but it did untill v.10.10

[..]Does anyone know if this works? I mean I don't want to try anything hazard that might break my system :D

---

### Post by owiknowi on 2011-10-19
@einov
for starters you could check if the file: **/etc/rc.local** still is used on your system...

---

### Post by einov on 2011-10-19
> **owiknowi said:**
> @einov
for starters you could check if the file: **/etc/rc.local** still is used on your system...
Yea it is and I did as you instructed but sadly it didn't work. Thanks for the effor though.

Do I really just have to wait for a new upower version or what? This sounds like a little bug but it is actually really annoying! :S

---

