---
title: "Disabled Unity"
date: 2011-09-24
forum: New to Ubuntu
---

### Post by BruceCM on 2011-09-24
Disabled the Unity option to try the others but now have lost the launcher down the left & the options along the top! So, how do I get back into the Compiz Settings to return it all, please?

---

### Post by Larkspur on 2011-09-24
This should(?) work even if Unity is switched off: Ctrl+Alt+T to open Terminal, then type "ccsm".

---

### Post by Blasphemist on 2011-09-24
Use these commands to reset all the settings in compiz.

gconftool-2 --recursive-unset /apps/compiz
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1

---

### Post by BruceCM on 2011-09-24
ctrl+alt+T doesn't seem to do anything, is there any other way to get a terminal up, please?

---

### Post by HuaiDan on 2011-09-24
Do alt-f2, then run "gnome-panel".
You should get your taskbar and menu button, then you can add "gnome-panel" to startup apps, if that would even be necessary.

---

### Post by Lisiano on 2011-09-24
This will give you a TTY, press Ctrl+Alt+F1-F6
Now after you login (Your password will not be visible when typing, not even ****) type this.
```
DISPLAY=:0.0 gnome-terminal
``` now just press Ctrl+Alt+F7

---

### Post by BruceCM on 2011-09-24
Login screen still same, where am I to type your command, please? After that, it's just the desktop!

---

### Post by Blasphemist on 2011-09-24
So I'm not hearing exactly what you do see. Do you get a login screen? If so choose the classic session, and open a terminal from the desktop. You could also use the threads first post for seeing ways to get a terminal. [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by BruceCM on 2011-09-25
All sorted now, thanks!

---

