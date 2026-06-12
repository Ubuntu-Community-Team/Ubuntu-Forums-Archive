---
title: "need help installing theme."
date: 2008-09-14
forum: New to Ubuntu
---

### Post by ludacrisman7 on 2008-09-14
ive been trying to install this screen saver lock theme... [http://www.gnome-look.org/content/show.php/Hacker+logo+lock+scren?content=89030]("http://www.gnome-look.org/content/show.php/Hacker+logo+lock+scren?content=89030") ...and i cant seem to get it to work. ive done what it has told me, but it still doesnt appear when my screen locks.

what can i do?

---

### Post by ludacrisman7 on 2008-09-14
please?

---

### Post by ChanServ on 2008-09-14
here :D
> 1. Unpack 1 folder 2 files to /usr/share/gnome-screehackver/
* ( directory hack-images lock-dialog-hack.glade lock-dialog-hack.gtkrc

2. Open gconf-editor (Alt+F2, type 'gconf-editor' and press enter) change the entry apps/gnome-screensaver/lock_dialog_theme from 'default' to 'hack'

3. Enjoy!

---

### Post by ludacrisman7 on 2008-09-14
it wont let me copy the files into usr/share/gnome-screensaver/

and im guessing unpacking is the same as extracting the files...?

---

### Post by ChanServ on 2008-09-14
> **ludacrisman7 said:**
> it wont let me copy the files into usr/share/gnome-screensaver/

and im guessing unpacking is the same as extracting the files...?

you need to do it as root

and yes

---

### Post by ludacrisman7 on 2008-09-14
what is root? im sorry im new to linux

---

