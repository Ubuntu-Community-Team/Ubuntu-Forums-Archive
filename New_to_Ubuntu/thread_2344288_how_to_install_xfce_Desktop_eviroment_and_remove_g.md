---
title: "how to install xfce Desktop eviroment and remove gnome ???"
date: 2016-11-23
forum: New to Ubuntu
---

### Post by hasan5599 on 2016-11-23
hello helpful guys..............

Now I am using Ubuntu 16.04 LTS which is gnome mood. But I want to remove gnome Desktop enviroment totally and want to install XFCE Desktop enviroment How to do it ???

---

### Post by Frogs Hair on 2016-11-23
Did you install Ubuntu Gnome to begin with ?

---

### Post by hasan5599 on 2016-11-23
Yes I fresh download and install 16.04 LTS so now I want to first install another I mean xfce desktop enviroment and then want to remove gnome mood ....

---

### Post by vasa1 on 2016-11-23
You have to be very careful in trying to "remove gnome mood". Many GNOME components can be removed but their removal may break your system. If you're new to Ubuntu (or Linux in general), you could have difficulty recovering your system.

If you've decided you like xfce, I'd suggest a clean installation of Xubuntu over whatever you have now (after backing your personal data).

---

### Post by hasan5599 on 2016-11-23
OK , if I want to keep both desktop enviroment I mean not removing Gnome Desktop and install Xfce4 desktop enviroment . Will it be safe for mine  ?? If be then give me a way how to install xfce4 desktop enviroment ...........Thanks

---

### Post by Frogs Hair on 2016-11-23
Edit : Yes, you can keep both , just disregard the remove Gnome section.


Backup before starting.

This is not the Xubuntu desktop so be sure xfce is what you want. 

To install xfce use the following and select the xfce session during login. ```
sudo apt-get install xfce4
``` ```
sudo apt-get install xfce4-goodies
```

Remove Gnome: ```
sudo apt-get remove ubuntu-gnome-desktop
```

---

### Post by vasa1 on 2016-11-23
```
sudo apt-get update
```then
```
sudo apt-get upgrade
```
and then, if there aren't any nasty warnings or errors,
```
sudo apt-get install xfce4
``` will give you what you want.

If you want something more elaborate, you could run ```
sudo apt-get install xubuntu-desktop
```

**And whatever you do, please stop using root needlessly. You will break your system if you don't know what you're doing.**

---

