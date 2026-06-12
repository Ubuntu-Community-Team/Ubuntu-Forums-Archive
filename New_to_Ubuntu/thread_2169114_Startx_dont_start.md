---
title: "Startx dont start"
date: 2013-08-20
forum: New to Ubuntu
---

### Post by Ry3cnmm on 2013-08-20
Hi,

i changed grub file because i want to start with text mode by default but when i want to change to graphical mode(startx), i am enable to see it because i have my mouse activate but i dont access completely to ubuntu.

Could you please help me?

thanks.

---

### Post by Ry3cnmm on 2013-08-20
my error said: 

xinit: connection to x server lost

---

### Post by Bashing-om on 2013-08-20
Ry3cnmm; Hi ! Welcome to the forum.

How one starts the GUI desktop varies in each distro and the desktop environment in use.
What distribution and version are you running ?
what desk top environment do you have installed ?

Off the top of my head, try:
```

sudo service lightdm start ## for unity
sudo service gdm start ## for gnome
startxfce4 ## for xfce4

```

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by Cheesemill on 2013-08-20
Can you also post the contents of your ~/.xinitrc file please.

---

### Post by Portaro on 2013-08-20
sudo update-alternatives --config x-session-manager

or 

edit 
~./xinitrc

---

