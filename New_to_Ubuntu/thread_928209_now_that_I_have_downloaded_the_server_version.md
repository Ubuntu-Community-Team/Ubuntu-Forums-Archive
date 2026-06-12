---
title: "now that I have downloaded the server version"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by jeff Odom on 2008-09-23
Now that I have downloaded the server version, how do I delete the text version of ubuntu that I downloaded and applied?

---

### Post by jimmy the saint on 2008-09-23
I think you are asking how to install the desktop version of Ubuntu now that you installed the server version? If that is the case log in and do 
```
sudo apt-get update
```

then

```
sudo apt-get install ubuntu-desktop
```

This will download a lot of stuff and install it.  When it is done, restart your machine and you will have the desktop version of Ubuntu (with a few extra server stuff as well)

---

### Post by jemate18 on 2008-09-23
Follow the above post and it will work....

However, if you want to run KDE or xfce,, you might as well type

for KDE
```
sudo apt-get install kubuntu-desktop
```


for XFCE
```
sudo apt-get install xubuntu-desktop
```

But having a lot of desktop environment is sometimes not good.. SO just choose ubuntu-desktop as you like GNOME.......

---

### Post by jamesrfla on 2008-09-23
Doing ```
sudo apt-get install xubuntu-desktop
``` or ```
sudo apt-get install kubuntu-desktop
``` will basically get you the everything that kubuntu or xubuntu comes with. If you just want a GUI do ```
sudo apt-get install xserver-
xorg gdm gnome-core xfonts-
base xterm pmount gnome-
mount synaptic -y
``` This will give you a ubuntu gui with synaptic packmanager.

---

