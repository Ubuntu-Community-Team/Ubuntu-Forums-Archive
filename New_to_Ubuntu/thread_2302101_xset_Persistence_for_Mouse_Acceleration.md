---
title: "xset Persistence for Mouse Acceleration"
date: 2015-11-07
forum: New to Ubuntu
---

### Post by charles61 on 2015-11-07
How can I make xset run at startup? I want to run the command: ```
xset m 3 0
``` I tried adding it to the end of /etc/X11/xinit/xinitrc, /etc/rc.local, and even ~/i3/config, but none work. Thanks!

EDIT: I'm using the i3 window manager, so no Gnome.

---

### Post by yetimon_64 on 2015-11-07
In dash type "startup". 

You will see "Startup Applications" in the results, click it to open "Startup Applications Preferences" > Press "Add" > Fill in "Name" and "Command" (put in "xset m 3 0" without the quotes used here for the command), add a comment if you wish then press "Add". 

You should now see your startup entry in the Startup Applications Preferences window. Do a log out/back in, or restart, to test the entry. Good luck, yeti.

---

### Post by charles61 on 2015-11-07
Sorry, I forgot to note that I'm using i3, so I can't use Startup Applications. Is there some script I can change? Thanks.

---

### Post by yetimon_64 on 2015-11-07
A desktop config file placed at "/home/<user>/.config/autostart" may possibly work, though I know absolutely nothing about the i3 windows manager or how it autostarts a process.

---

### Post by charles61 on 2015-11-07
It didn't work, but thanks.

---

