---
title: "PC Froze, Now no toolbars."
date: 2008-06-19
forum: New to Ubuntu
---

### Post by thegame310 on 2008-06-19
My computer froze, so I restarted, and now I have no top tool bar (with applications and things) and no bottom bar (with work spaces) 

any idea how  I can get them back?

---

### Post by vambo on 2008-06-19
In terminal try

```
xfce4-panel &
```

---

### Post by thegame310 on 2008-06-19
That worked! Thanks so much

---

### Post by yragrelluf on 2008-06-19
press ctrl + f2 and type in sudo apt-get gnome-panel, or sudo apt-get gnome-panel-applet. This is assuming you are using gnome.

---

### Post by thegame310 on 2008-06-19
when I do the xfce command, and I close termnial, my tool bars then close, anyway to have it where I can close terminal and still have my bars?

---

### Post by vambo on 2008-06-19
Couple of things.
You can run the command via <alt><F2> - Brings up the "Run Command" dialogue.
Also enable "Save Session for Future Logins" in your exit dialogue. This will bring up the panels at each login (assuming you have the panels running when you log out!!)

---

### Post by philinux on 2008-06-19
If you logged in you might try reinstalling 

ubuntu-desktop

From synaptic

---

