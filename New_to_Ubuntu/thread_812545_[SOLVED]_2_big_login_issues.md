---
title: "[SOLVED] 2 big login issues"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by sports fan Matt on 2008-05-30
AS spiderbatdad says I have a habit of breaking my system, its how we learn, right?

1.  I cant log into my gnome again..I get a real fuzzy screen and my mouse freezes..then I must reboot...

2.  I get a cant find usr/share/themes/human i guess folder..I just want to login to gnome if its possible and maybe LOCK IT DOWN HEH to prevent this...

Anyone want to take a stab at trying these and seeing if I can login without a reinstall?  The machine boots normally...Thanks in advance!

---

### Post by quelx on 2008-05-30
at the messy screen see if you can **CTRL-ALT-F1** and login

if so try ```
dpkg-reconfigure -phigh xserver-xorg
```

**/usr/share/themes/Human** --- capital **H**?

---

### Post by sports fan Matt on 2008-05-30
yes..says "cant open file" but since i deleted them (they were taking up space) although ive never seen that message before when they were deleted...Very interesting

---

### Post by quelx on 2008-05-30
were you able to get a prompt after **CTRL-ALT-F1**?  

```
sudo apt-get install human-theme
``` even from the console

---

### Post by sports fan Matt on 2008-05-30
I can do one better...im in failsafe gnome..I will try this out

---

### Post by sports fan Matt on 2008-05-30
human-theme is already the newest version.
The following packages were automatically installed and are no longer required 
libbeagle1 compizconfig-backend-gconf
And dpkg says: xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080530001416

---

### Post by quelx on 2008-05-30
how about ```
sudo apt-get --reinstall install human-theme
```

---

### Post by sports fan Matt on 2008-05-30
the same command..What i did to uninstall it was gksudo nautilus>usr/themes>human and it went poof..So i know i used root to get rid of it

---

### Post by quelx on 2008-05-30
You didn't uninstall human-theme, you just deleted it's files.  Ubuntu still thinks the package is installed, adding and removing packages must be done from **synaptic**, **apt-get**, or **aptitude** to keep you system in order.

What do you mean > the same command..? 
Did you add **--reinstall**

---

### Post by sports fan Matt on 2008-05-30
there we go, its setting up the human theme, i must have not copied it correctly..:) human theme solved! I tried a sudo apt-get remove then install ubuntu-desktop after dpkg-reconfigure -phigh xserver-xorg..im going to log out then try to login

---

### Post by sports fan Matt on 2008-05-30
I spoke too soon...that same message appeared..im going to get into symaptic and look around

---

### Post by sports fan Matt on 2008-05-30
The wierd thing is its installed (the human theme)..I wonder what in the world I did to not make my desktop login, yet everything is visible I believe

---

### Post by sports fan Matt on 2008-05-30
one thing i forgot to mention..i used the global menu hack found on googlecode which started my mess...Any idea if that has caused my problem?

---

### Post by sports fan Matt on 2008-05-30
Fixed by a reinstall..

---

