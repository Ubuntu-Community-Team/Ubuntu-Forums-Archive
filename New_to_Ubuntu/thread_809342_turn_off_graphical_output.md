---
title: "turn off graphical output"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by roboa1983 on 2008-05-27
Hi
If I'm going to be connecting a desktop only through ssh, is there a way to turn off all graphical output?
I tried to run it without a graphics card, but that does not work. I suspect, I need to set up my computer as a server. If so, do I only need to install the LAMP programs?

Thanks!!

---

### Post by ibutho on 2008-05-27
To stop the system booting into a gui, run Applications -> Accessories -> Terminal and enter the command
```
sudo update-rc.d -f gdm remove
```

---

### Post by roboa1983 on 2008-05-27
ibutho:
Will this stop the machine from looking to find a graphics card? Can it be reinstalled just as easily?

---

### Post by ibutho on 2008-05-27
I don't know if it will stop the machine from looking for a graphics card, but it will boot Ubuntu into the command line instead of GUI mode.

---

