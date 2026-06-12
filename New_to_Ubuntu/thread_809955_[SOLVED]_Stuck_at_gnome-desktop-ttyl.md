---
title: "[SOLVED] Stuck at gnome-desktop-ttyl"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by sports fan Matt on 2008-05-27
I cant log in cause i get this when I attempt to get to gdm--"gnome-desktop--ttyl"

I played with the [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491) and accidently disabled the gdm login (stupid I know), and it doesnt login.  Is there anything from the recovery console I can try to fix this???

Any help appreciated!

---

### Post by spiderbatdad on 2008-05-27
```
startx
```???

---

### Post by sports fan Matt on 2008-05-27
I was thinking the exact same thing and was going to post it and see if it would work...I'll try it now:)

---

### Post by sports fan Matt on 2008-05-27
that got me to the desktop, but im wondering if i can just reconfigure everything without reinstalling...additional info: could not fetch archives: when i tried to reinstall the gnome desktop with sudo apt-get install gnome-desktop or ubuntu-desktop

---

### Post by sports fan Matt on 2008-05-27
Since i was running not in an internet mode, I couldnt go back and remember how to fix steps i did when i borked it using that page..any ideas?

---

### Post by spiderbatdad on 2008-05-27
You seem to enjoy breaking your system constantly :) just like I do.
You seem to have a working machine. Try checking your sources list. Maybe this guide to building a kernel will help:[http://howtoforge.com/kernel_compilation_ubuntu](http://howtoforge.com/kernel_compilation_ubuntu)

IDK how to fix what you've done, especially if you can't remember what it was you did.

---

### Post by sports fan Matt on 2008-05-27
I tried to speed up the boot process using this guide...[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)
and when i got to step 17:17. gdm - The gnome desktop manager. I turned it off anyway since I get use to boot to console first. This is up to you if you want to boot directly to GUI. The default is 2,3,4,5

I simply unchecked all those boxes cause in my boot/grub/menu.lst, I erased the splash and quiet lines, making it text only, and now i cannot login, lol

---

### Post by spiderbatdad on 2008-05-27
have you tried ```
sudo init 2
```to get the defualt runlevel back?

---

### Post by sports fan Matt on 2008-05-27
through synaptic i saw everything was installed still using the residual config area so im hoping i can avoid castrophe ..the only thing that cant be installed is the gnome-desktop enviornment, but i did tell it to install ubuntu-desktop. Do you guys think im in the clear?

---

### Post by sports fan Matt on 2008-05-27
packages are reinstalling so this is a good sign:) wish me luck!

---

### Post by sports fan Matt on 2008-05-28
3 hours later..90 percent is fixed..i just went into the same forum and reinstated the gdm items i unchecked..

My question:  My gnome is a bit screwed up, its not properly loading..How can I reinstall the gnome part so I can use both gnome and XFCE if I choose to?

---

### Post by sports fan Matt on 2008-05-28
I can log into failsafe gnome, but with regular gnome, it freezes and no desktop and no cursor movement..Any ideas why it would fail this badly?

---

### Post by sports fan Matt on 2008-05-28
I FIXED IT TA DA!:)  I did a gnome restore to default and all is well:) 

Finished product:

---

