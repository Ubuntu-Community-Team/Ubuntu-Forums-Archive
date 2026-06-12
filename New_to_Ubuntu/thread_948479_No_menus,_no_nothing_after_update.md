---
title: "No menus, no nothing after update"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by macruadhi on 2008-10-15
I finally got Ubuntu installed (8.04 LTS) on my Dell E1505 laptop. I ran the suggested updates and restarted as required. Upon booting into Ubuntu, I had (I think) was a kernel panic. Actually I think I may have had some corrupted files and I was asked if I wanted to rewrite this and this, etc, (sorry, I didn't write it down, I was too distraught). After I did as it suggested, I rebooted into the previous kernel (2.whatever.16) and when it finished loading, I had a desktop, desktop icons, but no menu bar, no task bar. I thought maybe I had deleted them so I right clicked on the desktop and only got the options to change background, etc. I tried rebooting into the new kernel with the same results. 

I would really like to not have reinstall ubuntu as I finally have everything almost as I want it.

---

### Post by gjoellee on 2008-10-15
this may be a gnome-panel problem.
if you have gnome do added to startup you may launch gnome to and access the terminal and add the command:
```
gnome-panel
```

If that does not work try installing the package:
```
sudo apt-get install gnome-panel
```

if anyone knows any other way to turn on the gnome panels that might work as well...

---

