---
title: "&quot;Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.&quot;"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by leotemp on 2008-05-11
Using the NVIDIA settings application I am trying to config my second monitor (something ive been trying to get to work off an on for a couple weeks now), when I click the button "Save to X configuration File" I get this error

"Unable to create new X config backup file '/etc/X11/xorg.conf.backup'."

at first it told me it couldn't remove the old backup, so i manually removed it and now its telling me it cant create a new one, should i just delete the existing one, that seems bad :confused:

Any ideas why its not saving the file?

---

### Post by gila_monster on 2008-05-11
Is the NVIDIA settings application being run with sudo (i.e., did it ask for a password when you ran it)? That particular directory is protected, you need to save the file as root.

gila

---

### Post by macaholic on 2008-05-11
You could always jsut make a backup of it yourself. Something along the lines of this should do it:```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
Also you should probably run the nvidia settings thing with root privileges, with gksu .

---

### Post by leotemp on 2008-05-11
I dont believe it is, do i just change where the menu item for nvidia settings is pointed at IE put sudo in front of the application call?

---

### Post by inportb on 2008-05-11
> **leotemp said:**
> I dont believe it is, do i just change where the menu item for nvidia settings is pointed at IE put sudo in front of the application call?

Not sudo, but gksudo or kdesu depending on your desktop environment. (I assume it's a graphical app... right?)

---

### Post by macaholic on 2008-05-11
> **leotemp said:**
> I dont believe it is, do i just change where the menu item for nvidia settings is pointed at IE put sudo in front of the application call?
When running a graphical application, always use gksu instead of sudo, I don't know the nvidia settings command, but putting gksu in front of it should work.
EDIT: Gosh I am not doing well with these posts, I keep posting less then a minute after people. :p

---

### Post by leotemp on 2008-05-11
Im a Windows convert so i need a little hand holding, i tried to just edit what would be a shortcut to the menu item by right clicking but that doesn't appear to be the cheese. How would i go about editing that menu item or finding out what executable to call from the terminal?

---

### Post by inportb on 2008-05-11
First of all, are you on Gnome or KDE? On KDE (because I use it), you simply navigate to the menu item, right-click, select edit, make your changes, and save.

---

### Post by leotemp on 2008-05-11
Gnome

---

### Post by leotemp on 2008-05-11
Thanks guys, i found Alacarte and changed the the menu like you said and it saved the file correctly, now i can see if that will finally make my monitor go to the correct rez

---

