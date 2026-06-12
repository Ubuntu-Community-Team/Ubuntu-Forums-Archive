---
title: "hardy wont shut down"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by da3shot on 2008-05-31
hey guys, i just upgraded to hardy abt 4 days ago, but my problem started just yesterday. Whenever i try to shutdown my computer, it wont. i hit the shutdown button, but then nothing happens. everything still appears on the screen, but its almost like it freezes, but i can still move my mouse and everything. Anybody know how to solve the problem, or check for what might be wrong??

Thanks for the help

---

### Post by zenwalker on 2008-05-31
Its the problem with the power mgmt session process. Go to Sessions apps, and start that power mgmt if stopped. THe same hapnd 2 me 2.

---

### Post by Inxsible on 2008-05-31
Can you try the command line and see if that works?  ```
sudo shutdown now
```

---

### Post by da3shot on 2008-05-31
> **zenwalker said:**
> Its the problem with the power mgmt session process. Go to Sessions apps, and start that power mgmt if stopped. THe same hapnd 2 me 2.

u mean go to system->sessions->start up programs -> power management?? i did that, nd power management was already checked.

---

### Post by Matzy on 2008-05-31
hello. i've installed ubuntu 8.04 on my pc and porheps the only problem i really have is: when I want to Shut Down, I get the shutdown screen with the slidebar, and after it finishes, i can hear the sound of the source or something witch usualy is follawed by the Shut Down of the computer. well, in my case it dosen't. I have an asus P5AD2-E Deluxe mainboard with an Intel 4 CPU. (suspend works vrey badly, and hybernate pops an error report when waking up in witch the hybernation wasen't pleasing... :| )

thank you.

---

### Post by philinux on 2008-05-31
To save editing config files. Install startupmanager, then run it from System>admin.

On the first screen at the bottom tick the box

Show text during boot.

This also make the system show text at shutdown. You can look to see what error message come up during shutdown. Once you've solved the problem you can turn the text off easily.

---

### Post by shifty_powers on 2008-05-31
look

[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/123078](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/123078)

---

