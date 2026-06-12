---
title: "[SOLVED] Lost Desktop icons"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by driscom59 on 2008-09-07
Hi, I uninstalled Evolution and installed Thunderbird which was working nicely.  I turned off the computer for a couple of hours and when I turned it back on there is only the desktop and a couple of folders on the screen all of the toolbars (usually at the top of the screen) are gone!!!!!! Help!!!

---

### Post by firefly2442 on 2008-09-07
Did you maybe mistakenly change the permissions?  Your files/folders on the desktop might still be there just not visible.  Try opening up the terminal and typing:

```
cd Desktop
ls -l
```

This will list the files with the permissions.

---

### Post by niccholaspage on 2008-09-07
I think you need to keep Evolution.right click on the desktop>Create Launcher>Than type some name and for the command type:gnome-terminal.Now open it and type sudo apt-get install evolution.Now reboot with sudo shutdown -r now.

---

### Post by driscom59 on 2008-09-07
Hi have tried right click - create launcher but nothing happens. Next suggestion? Thanks for your time

---

### Post by driscom59 on 2008-09-07
Sorry unable to find the terminal

---

### Post by driscom59 on 2008-09-07
My folders are all still there but the toolbars are not.  How do I get into the terminal if I cannot access the toolbars?

---

### Post by Too Late on 2008-09-07
Press Alt+F2

---

### Post by driscom59 on 2008-09-07
tried that - nothing happened

---

### Post by driscom59 on 2008-09-07
Accidently found a recovery mode in the startup menu (I think thats what its called - the writing and countdown before it goes into the OS) so tried that and so far so good -thanks to all

---

