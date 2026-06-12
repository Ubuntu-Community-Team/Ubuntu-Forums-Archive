---
title: "shut down computer during updates"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by G_W on 2008-10-30
I shut down my computer while it was in process of installing updates thinking it would just shut off when it completed the updates but it just shut off right away.  When I turn the computer back on this morning, I could type in my username and password just fine but when it came to the main screen it is just a blank white screen.

---

### Post by ibizatunes on 2008-10-30
Reboot
in the grub menu select recovery mode 
then drop into the terminal 
do sudo apt-get update && apt-get upgrade

then sudo shutdown -r now
in the grub menu select recovery mode 
then select repair your xorg (i cant remember this bit of commands im at work)

then you should be able to boot fine!!

---

### Post by eternalnewbee on 2008-10-30
So, what did you do next?..

---

### Post by G_W on 2008-10-30
the husband is having me do this so i know how what or how do you get to the grub menu

---

### Post by unoodles on 2008-10-30
When the system is booting, and you see the screen that says Grub, hit ESC.

---

### Post by G_W on 2008-10-30
thanks guys and gals it worked perfectly!!!

---

