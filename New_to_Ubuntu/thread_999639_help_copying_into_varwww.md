---
title: "help copying into /var/www/"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by ja660k on 2008-12-02
hey guys im having trouble with var/www

i move my html in there...
using the cmd line. sudo mv 

but when i go to firefox and localhost it comes up with a file to save.
called PHTML and i open it and its the homepage

this is really fustrating.

i got it working before then i switched to a newer laptop and now it doesnt work

please help

i chanegd permission to 777 on the actuall www folder and all files in it

i know its bad. but i need this resolved somehow.

---

### Post by Liviu-Theodor on 2008-12-02
I know two other ways to do it:
1. Run in a terminal:
```
gksudo nautilus /var/www
```
if you use ubuntu, or for kubuntu:
```
kdesu dolphin /var/www
```

2. If you prefer not using the command line:
in Synaptic/Adept, install [FONT="Courier New"]nautilus-gksu[/FONT].
After, that, just ope normally the [FONT="Courier New"]/var[/FONT] folder, right-click on the www folder, and there you have the [FONT="Courier New"]Open as administrator[/FONT] option.

---

### Post by the yawner on 2008-12-02
What webserver were you using? And have you tried restarting the webserver?

---

### Post by ja660k on 2008-12-02
im using apache, with a little playing i found out i forgot to install php :(


thanks anyway

---

