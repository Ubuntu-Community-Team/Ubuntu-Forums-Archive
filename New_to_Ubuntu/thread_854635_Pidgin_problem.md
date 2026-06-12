---
title: "Pidgin problem"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by xenos90 on 2008-07-09
I cant launch pidgin from the desktop, and when I try to launch from terminal ./pidgin i get this error:
 (pidgin:6520): Gdk-CRITICAL **: gdk_display_get_name: assertion `GDK_IS_DISPLAY (display)' failed
Pidgin 2.4.1
This is pidgin that came preloaded with Ubuntu Hardy Heron on a Dell XPS with Ubuntu preinstalled.
THanks for any help I get.
Apparentlyl I can see IMs but i cant see the buddy list

---

### Post by Het Irv on 2008-07-09
Open your home folder and press "Ctrl+H".  Then scroll till you see the folder ".purple"  copy that entire folder to your desktop.  This folder contains all of your settings.  If we keep a backup, it will be easier once the problem is solved.

Next open the terminal "Applications - Accessories - Terminal" and type
```
sudo apt-get remove pidgin
```

Once that finishes type ```
sudo apt-get install pidgin
```

Can you open pidgin now?

---

### Post by xenos90 on 2008-07-09
No I cant, but it seems like i am logged in but i cant see the buddy list

---

### Post by adieb on 2008-07-09
are you sure that pidgin is not just running in system-tray mode.
click on the icon in the notification area.
does it open?

---

