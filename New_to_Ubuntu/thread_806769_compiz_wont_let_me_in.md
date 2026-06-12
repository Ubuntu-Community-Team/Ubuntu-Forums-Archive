---
title: "compiz wont let me in"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by Mick8882003 on 2008-05-25
I was messing with the graphics (set the cogs graphic on) now when i go to log in the comp crashes before I can get in to change any settings, I have another account, but how do I turn off the graphics from the other account, or ne other way for that matter... thanks

---

### Post by sayakb on 2008-05-25
Press Ctrl+Alt+F1 at GDM to enter tty0 and login. Then do:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Mick8882003 on 2008-05-25
tried setting the framebuffer and not, neither one worked.

---

### Post by sayakb on 2008-05-25
Did you make any changes to the xorg.conf file. If so, boot in through the recovery mode and replace the existing one with the auto generated backup file (replace xorg.conf with xorg.conf.backup/xorg.conf~ whichever applicable)

---

### Post by ajgreeny on 2008-05-25
Using gnome just open a terminal and use ```
metacity --replace
``` to turn off compiz for now, at least.  You can now change the configuration of compiz to get it working again.

EDIT--  Whoops, sorry, I see you cant log in at the moment.  I have no idea what will happenif you go to tty1 with Ctrl+Alt+F1 and then try the code I gave, but it's worth trying.

---

### Post by Mick8882003 on 2008-05-25
swapped the config file out and still no good

---

### Post by Mick8882003 on 2008-05-25
bump

---

