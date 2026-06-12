---
title: "[SOLVED] graphics card help"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by mikedemario17 on 2008-07-22
i have Ubuntu 8.04 LTS and i want to get Compiz Fusion on it.

this is my out put of my graphics card....

mike@mike-desktop:~$ sudo lshw -short | grep display
/0/100/1/0 display NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]
mike@mike-desktop:~$

........
when i go to System -> Administration -> Hardware Drivers there is nothing in the Hardware Drivers window??? its just blank....

can some1 tell me how to get Compiz Fusion working with what i got...
or a down load to update my graphics card? :confused:

---

### Post by ajgreeny on 2008-07-22
I don't think it is possible with that card from what I've seen after a quick google.

---

### Post by mikedemario17 on 2008-07-22
what can i do to get themes on my pc then?...to make it look smooth and not boxy...?

---

### Post by ajgreeny on 2008-07-22
Go to [http://gnome-look.org/](http://gnome-look.org/)

---

### Post by mikedemario17 on 2008-07-22
after i installed some of the themes firefox is sllllloooooowwwww and frezes every 5 min... did i get a virus or something?

---

### Post by ajgreeny on 2008-07-23
No, there are no viruses in linux.  I suspect the problem is still your graphics card, I'm afraid, and I can't help any more with it as far as a driver is concerned.  Go to Screens and Graphics with ```
gksudo displayconfig-gtk
``` and see what driver is in use at the moment, and try others if you can in the ati section.

---

### Post by mikedemario17 on 2008-07-24
yeah my graphics card is a 2-d and cant support it....but whats weird is when i installed 7.10 again coz 8.04 is slow as sh*t on my pc and it cant handle 8.04...and i tried to do it just for fun...and no error popped up under restricted drivers when i went to activate the high performince card... so i restarted and all the settings poped up for it.! but when i switched my card to custom...it says it cant be supported... so im just waiting for a new pc to put the hard drive in...

---

