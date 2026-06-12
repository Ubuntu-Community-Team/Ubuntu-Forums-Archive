---
title: "Cannot access any folders in GUI and desktop icons have disappeared... Help plz!"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by comprendrelinux on 2008-09-18
Hi! 

After trying to put 4 wallpapers on each side of the cube following this post [http://forum.compiz-fusion.org/showthread.php?t=6199](http://forum.compiz-fusion.org/showthread.php?t=6199) I broke nautilus and now I cannot access my folders(home folder, /media, ...).

My desktop icons have also disappeared and when I right click on my desktop to change background for example nothing happens(no window opens).

Can anyone help? 

PS:I'm on Hardy Heron 8.04

> nautilus

Initializing nautilus-share extension
Initializing nautilus-image-converter extension
Initializing nautilus-open-terminal extension
seahorse nautilus module initialized
Segmentation fault

---

### Post by whizbaby on 2008-09-18
Go to a non-graphical terminal (eg by hitting ctrl-alt-F1) and try
Try
```
sudo apt-get remove nautilus --purge
sudo apt-get install nautilus
sudo /etc/init.d/gdm restart
```
In the thread you posted nautilus is removed first via apt-get, so this doesnt seem to present problems. So just removing the installed version and reinstalling from the repositories should solve your state. If not I cant help you further to solve, but I can suggest doing
```
sudo apt-get install xubuntu-desktop
```
then reboot your machine and choose a 'xfce4' session at the login screen and login. Its not gnome, but at least you would have a working desktop until you solved your gnome problems, and xfce isnt so bad at all.

---

### Post by whizbaby on 2008-09-18
Sorry but I forgot something: if the apt-get command cant remove nautilus, do it with dpkg
```
sudo dpkg -r nautilus
```

---

### Post by comprendrelinux on 2008-09-18
Do you know how to re-install from repository? I tried to install nautilus_2.22.3 for hardy but still doesn't work... 

I installed Konqueror yesterday to be able to access the files but still i would like nautilus to work properly on gnome....

---

