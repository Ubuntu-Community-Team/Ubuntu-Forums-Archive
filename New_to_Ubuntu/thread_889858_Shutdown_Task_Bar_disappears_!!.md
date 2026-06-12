---
title: "Shutdown: Task Bar disappears !!"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by chinnaraaju on 2008-08-14
hi,

when i press the shutdown option in desktop, the task bar( i dont know its specification in ubuntu) suddenly disappears. i am not able to shutdown my system thereafter.
Please help me to avoid this. or is there any tool to handle shutdown process.?

Regards,
Chinna.

---

### Post by knightcoder on 2008-08-14
If you press Ctrl+Alt+Delete, you'll get the options to reboot,shutdown,logoff and suspend.

---

### Post by chinnaraaju on 2008-08-14
hi..
i tried it but its not working in ubuntu in the sameway of windows..

Regards,
Chinna.

---

### Post by diwas on 2008-08-14
Alternatively u can shutdown throught Terminal: (Applications>Accessories>Terminal)
```

sudo shutdown -h now

```

If u need to reboot, type this in Terminal:
```

sudo reboot

```

This is how i do it...and its kinda fast too!! lol

---

### Post by chinnaraaju on 2008-08-14
Hi diwas,

i think GUI is more flexible than command terminal..
moreover, everytime u have to su root to do that shutdown process in terminal...

Regards,
Chinna.

---

### Post by LowSky on 2008-08-14
Shutdown is in two places. On the panel and under the System Menu.
If the one on the panel is broken just remove it and replace it, by right clicking on the panel click on add applet

---

### Post by diwas on 2008-08-14
Yes, it is. 
But Im actually used to it. 
Sorry!! 

Cheers!

---

### Post by chinnaraaju on 2008-08-14
i decided to use the one which is in system menu.!!
Thanks to all!!!!

---

### Post by diwas on 2008-08-14
You should mark this post as "solved" then.

Have fun!

---

### Post by knightcoder on 2008-08-15
You can also do a quick reboot with Ctrl+Alt+Bksp if you choose to do so.
Be sure to save your data before you do this since all programs are terminated without asking.

---

### Post by Lynette on 2008-10-07
Ctrl+Alt+Delete doesn't work for me, nor can I get my taskbar back. I rebooted and tried to use the shutdown button in the system menu but that also resulted in my taskbar vanishing. Is there any way I can get my task bar back?

---

### Post by tarps87 on 2008-10-07
If this is gnome try alt+f2 to open a console or ctrl+alt+F1 and log in. Type ```
gnome-panel
```
ctrl+alt+bkspace will force a reset, also pressing the pc's power button usually brings up the actions/shutdown menu.
You may need to add gnome-panel to the session file

---

