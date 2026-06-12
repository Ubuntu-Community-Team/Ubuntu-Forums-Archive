---
title: "XScreen Saver daemon"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by gulmer on 2008-07-24
Is there a way to get the XScreen Saver daemon to start up when I log onto my desktop,being KDE?I have to turn it on manually each time to get the screen saver to work. I'm using KDE4.

---

### Post by Zill on 2008-07-24
Open a file manager (eg Konqueror or Dolphin) and then, using the View menu, show "hidden" (dot) files in your home directory.

Locate the .kde directory and open the Autostart sub-directory.

Drag Xscreensaver from the "K" menu to the .kde/Autostart directory window, choosing the "link" option.

Logout and login again and Xscreensaver should start up automatically.

Caveat: this is all from memory and based on KDE3 so I may have got things *slightly* wrong :-)

---

### Post by gulmer on 2008-07-25
> **Zill said:**
> Open a file manager (eg Konqueror or Dolphin) and then, using the View menu, show "hidden" (dot) files in your home directory.

Locate the .kde directory and open the Autostart sub-directory.

Drag Xscreensaver from the "K" menu to the .kde/Autostart directory window, choosing the "link" option.

Logout and login again and Xscreensaver should start up automatically.

Caveat: this is all from memory and based on KDE3 so I may have got things *slightly* wrong :-)



   Thanks Zill, this worked with a little tweaking.KDE4 is a little different.             :)

---

