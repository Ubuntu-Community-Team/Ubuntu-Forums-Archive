---
title: "Nvidia X sever setting problem"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by the fish on 2008-05-04
so i was trying to get my TV output to work.  i reconfigure it to what i wanted, but now it wont let me save anything or go back to the way i had it setup. i am down to one screen and no TV. somebody i need help.

---

### Post by the fish on 2008-05-04
this is what keep comeing up

"Unable to create new X config backup file '/etc/X11/xorg.conf.backup"

---

### Post by m_duck on 2008-05-04
You can solve this by: Pressing alt + F2 and type **gksudo nvidia-settings** and press enter. Put in your password and this will run the program, then do as you were doing and it should all work! I thnk it's just the program needs root permissions to edit the files.

---

### Post by the fish on 2008-05-04
that was it. thanks!!!!!

---

