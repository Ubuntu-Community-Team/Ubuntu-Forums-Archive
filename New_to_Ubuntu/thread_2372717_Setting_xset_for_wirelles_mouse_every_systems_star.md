---
title: "Setting xset for wirelles mouse every systems startup"
date: 2017-09-28
forum: New to Ubuntu
---

### Post by kornixpl on 2017-09-28
Hi guys, i've got a problem. Mine mouse is too speed. I read some articles, threads and I set it by command [I]xset m 1 1.
[/I]
But after system reboot this setting is reset to default. How to set it forever?

---

### Post by yetimon_64 on 2017-09-28
I am assuming you are on a Unity desktop.

Open dash (very top icon on the unity side launcher) and type in "startup". 
In the "Applications" section just below where you type it in 2 icons should show up, choose (click on) "Startup Applications" and a new window will open.

Click on the "Add" button there and another window will open; fill in your details in this next window ...
Give the startup entry a name, for example "Mouse Start".

Put your command (*xset m 1 1*) in the "Command" section and if you want add a description in the last section (optional). Then lastly click the "Add" button when all your details are completed.

Next time you log out and log back in or reboot your install your mouse settings should be activated by your new startup entry you've just created.

If you are not on a unity desktop let us know, the procedure may vary slightly but a startup entry will be needed for such a command to be activated on each boot/login.

Regards, yeti.

---

### Post by TheFu on 2017-09-28
Put those commands into your desktop automatic startup location.  This is dependent on which desktop you are running.  I use openbox, so those commands would be placed into ~/.config/openbox/autostart.  That file needs to have execute permissions (chmod +x).  Any method that works outside a GUI login won't work.  It has to happen as part of the X/Windows session + window manager startup.

So, if you post your desktop environment, perhaps someone can help?

---

