---
title: "[SOLVED] Make gnome the default session"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by adobrakic on 2008-06-26
I made KDE the default session, and when I change it to gnome at login screen, it doesn't ask me if i'd like to make gnome default. Is there another way to do this?

---

### Post by philinux on 2008-06-26
System>Admin>Login Window

---

### Post by pytheas22 on 2008-06-26
In Gnome, go to System>Administration>Login Window.  Under the "General" tab you can select the default session.

---

### Post by adobrakic on 2008-06-26
I get this popup when i try to run that:
[img]http://img165.imageshack.us/img165/7948/screenshotgdmsetupqp8.png[/img]

---

### Post by ChompTheMan on 2008-06-26
Open up a terminal and type in:

```
kdesu kate /etc/X11/default-display-manager
```

and you should see:

```
/usr/bin/kdm
```

change it to:

```
/usr/bin/gdm
```

and save.  This should work.

---

### Post by dizee on 2008-06-27
Apparently KDE's login manager kdm makes the last session you logged into the default one automatically. You could test it anyway and if it doesn't, then try the changing to gdm as per the instructions given above.

---

### Post by kowe on 2009-11-17
I had problems with kdm and gdm as well.

If you're trying to get back to gdm from kdm and all above doesn't work you could also try:

Sudo dpkg-reconfigure kdm > press OK and choose between kdm and gdm

or try:

sudo -i
gedit /etc/X11/default-display-manager

change in /usr/sbin/gdm

good luck!

---

