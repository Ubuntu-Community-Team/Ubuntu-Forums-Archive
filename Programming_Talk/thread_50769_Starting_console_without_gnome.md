---
title: "Starting console without gnome"
date: 2005-07-21
forum: Programming Talk
---

### Post by index_0@ya.com on 2005-07-21
Hi thr, 
          I wanted to know how can i stop at  the console without x-server starts loading the gnome .. I sometimes wanted to work in console evry time of booting instead in the gnome.

---

### Post by NoTiG on 2005-07-21
WHy are you posting this in programming? 

You have to change the run level from 5 to 3 . 

sudo gedit /etc/inittab

edit the line
CODE
id:5:initdefault:

to your liking, save and reboot..

---

### Post by LordHunter317 on 2005-07-21
That doesn't work on Debian and Ubuntu.

---

