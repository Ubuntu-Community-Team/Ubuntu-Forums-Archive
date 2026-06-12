---
title: "Sudo command help"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by Mr.ClowN on 2008-08-01
Hi guys im new to the Ubuntu Forums & new to Ubuntu Linux.

Just a small question, does anyone know how to edit files owned by Root using the sudo command? example: sudo edit file /etc/file.conf.

appreciate the help.

Thanks.

---

### Post by mcduck on 2008-08-01
```
sudo nano /path/to/file
gksudo gedit /path/to/file
```
The first one uses command-line text editor nano, the second one uses graphical text editor Gedit.

---

### Post by Mr.ClowN on 2008-08-01
Thank you so much.

---

### Post by billgoldberg on 2008-08-01
OR

```
gksudo gedit
```

To open gedit as root, so you could open as many files you want to edit.

Or "gksudo nautilus --no-desktop" to open the file manager as root, so you could also open and edit whatever you want.

---

### Post by ingeva on 2008-08-01
Just a little question:
What's the difference between sudo and gksudo? Both seem to work the same here.

---

### Post by silkstone on 2008-08-01
**Always** use gksudo to open graphical applications (e.g. gedit, nautilus) as root. Never use sudo or you can mess up permissions.

Use sudo to run terminal commands as root.

---

### Post by mcduck on 2008-08-01
> **ingeva said:**
> Just a little question:
What's the difference between sudo and gksudo? Both seem to work the same here.

Sudo doesn't load root user's environment correctly for graphical applications (in some cases this results, for ecxample, program sto use your own user's setting files instead of roots, changing their ownership to root and making you unable to log in to desktop), and also requires you to run the command in a temrinal so you can input the password.

Gksudo works correctly for graphical applications, and provides you with a small window where you can give your password.

With some graphical programs sudo works fine, with others you'll get rather nasty problems. It's just beter to learn the habit of _always_ using gkasudo for graphical apps, as it's a lot easier than trying to figure out which programs need it and which don't.. :)

---

### Post by ingeva on 2008-08-01
> **mcduck said:**
> With some graphical programs sudo works fine, with others you'll get rather nasty problems. It's just beter to learn the habit of _always_ using gkasudo for graphical apps, as it's a lot easier than trying to figure out which programs need it and which don't.. :)


Great! Thanks!

---

