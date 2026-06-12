---
title: "Turn X11 off"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by Bakerconspiracy on 2008-10-29
Does anyone know how to turn X11 off without logging out? Using 8.04 Gnome. Thanks in advance.

---

### Post by w4ett on 2008-10-29
Try this:

> 
sudo /etc/init.d/gdm stop

---

### Post by bibleman on 2008-10-29
You could always go to one of the terminal screens (Ctrl+Alt+1-4) and login there. From there you could run ps -ax which would show you all of the currently running processes. There should be one name xinit. Locate the process number and run a the command kill NUMBER.
This will kill the xserver. If you need to restart it you could then run startx or simply reboot.

---

### Post by macogw on 2008-10-29
No, if you're logged in inside the GUI, getting rid of the GUI will always log you out. The solution is to login in the TTY instead, then stop gdm as mentioned above.

---

### Post by Bakerconspiracy on 2008-10-29
Yea. Thanks bibleman. I forgot about the old terminal trick. Anyways broke my X11 haha. Something wrong with the nvidia kernel module I compiled. Thanks again.

---

