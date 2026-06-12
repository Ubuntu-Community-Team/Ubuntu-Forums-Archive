---
title: "only loads in low graphics mode"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by WinterMadness on 2008-08-15
and on top of that, i cant change sessions. only gnome will load.
it has the ubuntu screen with the progress bar, then it goes to the terminal and says no image to load and a few seconds later my graphical login screen will come up but in a very bad resolution and just bad graphics.

any idea what this is?

I really think i had a bad install which gave me a bunch of problems, but id like to get this fixed.

---

### Post by Crafty Kisses on 2008-08-15
Have you tried reconfiguring X?
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by WinterMadness on 2008-08-15
im just replying for anyone who happens to get this problem in the future, i managed to fix it. 

luckily xorg.conf backs its self up in the same folder (x11)
it will be xorg.conf.(random numbers)

go into the terminal

```

sudo gedit /etc/X11/xorg.conf

```

what you wanna do is, find the backup and replace all the info in the original xorg.conf and save it, restart.

---

