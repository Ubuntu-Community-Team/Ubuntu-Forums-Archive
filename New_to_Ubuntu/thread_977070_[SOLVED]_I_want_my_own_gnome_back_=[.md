---
title: "[SOLVED] I want my own gnome back =["
date: 2008-11-09
forum: New to Ubuntu
---

### Post by CJ Master on 2008-11-09
Hello,

I messed around with my gnome toolbar settings to try to change it up a bit.... but now I hate it.

Is there any package or such to make it look like the default that comes with ubuntu? If not, could someone screen-shot their desktop so I can mimic it?

Thanks in advance!

---

### Post by Bölvaður on 2008-11-09
What is this "toolbar" ?

Is it the panels? the bars with come default on top and bottom of the screen.

---

### Post by Durden on 2008-11-09
Easiest way is to open a terminal and 'rm -rf .gnome"

It'll go back to the defaults entirely.

---

### Post by CJ Master on 2008-11-10
> 
What is this "toolbar" ?

Is it the panels? the bars with come default on top and bottom of the screen.

Yea.

> Easiest way is to open a terminal and 'rm -rf .gnome"

It'll go back to the defaults entirely.

Thanks for the adivise! But, not that I don't trust you or anything, but can someone please confirm that does what its supposed to? Sorry, I'm pretty paranoid when it comes to rm. :P

---

### Post by Ryadt on 2008-11-10
Try removing the panel and reinstalling it.
```
sudo apt-get --purge remove gnome-panel
``````
sudo apt-get install gnome-panel
```

---

### Post by CJ Master on 2008-11-10
> **Ryadt said:**
> Try removing the panel and reinstalling it.
```
sudo apt-get --purge remove gnome-panel
``````
sudo apt-get install gnome-panel
```

Wouldn't work unless I wanted to uninstall my ubuntu-desktop along with it.

---

### Post by EXCiD3 on 2008-11-10
removing .gnome should work, but first try Alt-F2 and run gnome-panel. Hopefully that works first and you dont have to reset gnome's config.

---

### Post by Ryadt on 2008-11-10
> **CJ Master said:**
> Wouldn't work unless I wanted to uninstall my ubuntu-desktop along with it.
Install the ubuntu-desktop package then.

---

### Post by Ptero-4 on 2008-11-10
> **CJ Master said:**
> Yea.



Thanks for the adivise! But, not that I don't trust you or anything, but can someone please confirm that does what its supposed to? Sorry, I'm pretty paranoid when it comes to rm. :P

It basically deletes the config files that holds the gnome configuration. Deleting them causes gnome to put the default ones in restoring the panels to factory defaults.

---

### Post by zvacet on 2008-11-10
First you have to stop gdm 

```
sudo /etc/init.d/gdm stop
```

Ctrl+Alt+F2

```
rm -rf .gconf* .gnome* .nautilus*

sudo reboot
```

---

