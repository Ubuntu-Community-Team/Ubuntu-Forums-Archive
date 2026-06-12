---
title: "How to install new themes on Ubuntu 12.04"
date: 2012-06-06
forum: New to Ubuntu
---

### Post by MrBledi on 2012-06-06
Hello people, please could tell anyone a newbie like me how to install new themes and where to get them? :)
Thanks in advice, Mr-Bledi

---

### Post by zombifier25 on 2012-06-06
There are loads of themes on [http://gnome-look.org/](http://gnome-look.org/) . Category GTK3 for themes. Most themes usually comes in a tarball, so extract the tarball into /usr/share/themes (if you want the themes to be available to all) or ~/.themes (if you want it to be available for you only). Note that ~ is your home directory and you may need to create the hidden .themes folder if you don't have it.

Then install a tool like myunity (available in the repos) and it will allow you to change GTK themes (which will change the look and feel of the windows) and windows border/Metacity themes (which will change the titlebar)

---

### Post by Frogs Hair on 2012-06-06
If you are using 12.04 use Gnome 3.4 themes . That will be indicated in the theme description.

---

### Post by MrBledi on 2012-06-06
thanks everyone!

---

### Post by MrBledi on 2012-06-06
i wanna copy paste this bridge folder to the usr/share/themes, that included themes inside but it says to me that i don't have permissions, so i thought to go into themes folders to properties to change the chmode to 666 or something, but it says that i'm not the owner, what to do?? THANKS!

---

### Post by zombifier25 on 2012-06-07
Do not chmod anything. That folder is owned by root, so only root can modify it. You can open the file manager as root:
```
gksudo nautilus
```
and do your work.

---

### Post by traditionalist on 2012-06-07
There are some nice themes here;

[http://www.webupd8.org/search/label/eyecandy?max-results=10](http://www.webupd8.org/search/label/eyecandy?max-results=10)

install PPA's at your own risk!  I have installed these without any problems.

---

### Post by philinux on 2012-06-07
> **MrBledi said:**
> i wanna copy paste this bridge folder to the usr/share/themes, that included themes inside but it says to me that i don't have permissions, so i thought to go into themes folders to properties to change the chmode to 666 or something, but it says that i'm not the owner, what to do?? THANKS!

Just put the new themes in the the hidden .themes folder in home. Install myunity from the software center and use it to select the theme you need.

---

### Post by charlier653 on 2012-11-05
But what if you don't like and won't use unity? It appears as though all the themes for 3.4 are usable only in unity. What must I do to use gtk-2.0 style themes such as clearlooks in 12.04? What commands will enable the use of other themes besides the 4 that pack with the upgrade?

---

