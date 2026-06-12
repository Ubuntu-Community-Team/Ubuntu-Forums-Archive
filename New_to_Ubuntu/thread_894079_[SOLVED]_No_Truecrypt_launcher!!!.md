---
title: "[SOLVED] No Truecrypt launcher?!?!?!?"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2008-08-18
I just installed Truecrypt (loving it by the way!) via the .deb package on their website, but I have to launch it via the terminal.  I don't seem to have a launcher in my Applications or System menus.  Is there a way to create one?

Thanks is advance!

---

### Post by stmiller on 2008-08-18
Right click on Applications ??!

---

### Post by pi.boy.travis on 2008-08-18
I checked the Edit Menus dialog, no Truecrypt. . .   I have restarted since installation as well. . .   Sorry, I should have clarified.

Is there a way to create one?

---

### Post by nicedude on 2008-08-18
You could make a menu bar launcher that loads it.

---

### Post by pi.boy.travis on 2008-08-18
Isn't the Truecrypt installer supposed to create one?  How would I go about creating a menu bar launcher?

---

### Post by doas777 on 2008-08-18
ok, right click on you applications button and select Edit Menus.

on the left pane, select the group in which you wish the launcher to appear.

on the right, click New Item. the Create Launcher window will appear.

name: truecrypt
command: truecrypt
comment: encrypts stuff. Kool!

click Ok.

now you should have a launcher for the app in your menu. after that, you can drag it to a panel, or just use it from where it is. The truecrypt installer did not try to make a shortcut, nor should it. if it did you would need a separate installer for gnome, kde, whatever, and x. 

good luck,
franklin

---

### Post by doas777 on 2008-08-18
nothing to see here.

---

### Post by pi.boy.travis on 2008-08-18
> **doas777 said:**
> ok, right click on you applications button and select Edit Menus.

on the left pane, select the group in which you wish the launcher to appear.

on the right, click New Item. the Create Launcher window will appear.

name: truecrypt
command: truecrypt
comment: encrypts stuff. Kool!

click Ok.

now you should have a launcher for the app in your menu. after that, you can drag it to a panel, or just use it from where it is. The truecrypt installer did not try to make a shortcut, nor should it. if it did you would need a separate installer for gnome, kde, whatever, and x. 

good luck,
franklin


EXCELLENT!!!  Thanks!

---

### Post by twizler on 2008-08-28
SOLVED nicely -- THX

---

