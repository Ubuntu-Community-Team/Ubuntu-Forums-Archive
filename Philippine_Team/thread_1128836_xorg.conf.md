---
title: "xorg.conf"
date: 2009-04-18
forum: Philippine Team
---

### Post by Lila_IT_CMU on 2009-04-18
how to edit xorg.conf????

---

### Post by neu2buntu on 2009-04-18
open "terminal and do command (then press enter) ```
gksu gedit /etc/X11/xorg.conf
``` type your password (wont show as characters) and enter > edit the file and make sure to save...

---

### Post by pbpersson on 2009-04-18
Do you want to know how to get in to edit the file or what values to change to reach a desired goal?

Before you change the file, make a backup:
```

cd /etc/X11
sudo cp xorg.conf xorg.mybackup
```

Then you are ready to actually get in there and edit the file:

```
gksudo gedit xorg.conf
```

If you do something totally wrong and when you reboot you only have a command prompt you can go to the directory, rename the new one to a save name, rename your backup to the real name, and type xstart to start the XServer and you should be back to where you started

---

