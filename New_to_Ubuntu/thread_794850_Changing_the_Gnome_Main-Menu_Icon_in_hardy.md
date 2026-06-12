---
title: "Changing the Gnome Main-Menu Icon in hardy?"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by BOBSONATOR on 2008-05-15
Hey guys, I just hopped back onto the ubuntu boat after a month or so, and was wondering how you change the gnome-main-menu or distributor logo, 

Thanks.

---

### Post by EXCiD3 on 2008-05-15
THe file should be /usr/share/pixmaps/gnome-logo-icon-transparent.png, change it to whatever you like! Most icon themes will modify this too, if you prefer to change it that way.

---

### Post by warbread on 2008-05-15
Alternatively, press ALT+F2 and type in gconf-editor.  From there, find Apps -> Panel -> Objects.  The main menu should be Object_0, but it can change if you've removed it and then added it again.  On the right side, scroll down until you find a check box labeled "Use Custom Icon" and check it.  A few lines above you will see an empty entry for "Custom Icon".  You can put in the path to whatever icon you want to use here.  This way you don't overwrite anything.

---

### Post by PinkFloyd102489 on 2008-05-15
Just for reference, the default icon is /usr/share/icons/hicolor/48x48/apps/distributor-logo.png

---

### Post by im_canadian on 2008-06-14
I tried everything that was listed here and nothing has worked at all. I am still stuck with the stock icon. What am I do wrong here?

---

