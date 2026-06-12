---
title: "Screen Scrambled"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by mrthundercleese4 on 2008-05-11
I have this odd problem where when i boot my computer everything is fine i login put my password in then the screen turns black for a second and then Ubuntu loads it is scrambled and i can't see a thing. This is 7.10 any idea what this is and how to fix it?

I had been using Ubuntu for months and no problems it just happened one day.

---

### Post by spiderbatdad on 2008-05-11
possibly due to an upgrade. try booting in safe graphics then look for a restricted driver in the restricted drivers section of System>>Administration

---

### Post by mrthundercleese4 on 2008-05-12
it won't let me boot in safe graphics mode i can only boot into the terminal, or windows.

---

### Post by mrthundercleese4 on 2008-05-20
Is there a way to reset the graphics settings from the terminal?

---

### Post by Zularan on 2008-05-20
Is it locking up as well as being scrambled?

Are you running Compiz or anything?  So after you plug in your password and it goes to load gnome it goes crazy right..  I'd probably start with  checking out your /etc/X11/xorg.conf to make sure everything looks right.  

Modifying that file is the only way I can think of resetting the graphics at the terminal.  
Another option is to reinstall your graphics drivers (Nvidia/ati).

---

