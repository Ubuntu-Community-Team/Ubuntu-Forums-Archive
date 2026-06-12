---
title: "startx alternative?"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by Delta62 on 2008-08-18
Hi everyone

I just installed kubuntu to check it out, but since it's not runniong on X (it's running on K), what would the alternative to startx be?

---

### Post by meanburrito920 on 2008-08-18
I'm sort of confused about what you are asking here. startx is the command to start the X11 server, which basically == the GUI, because the GUI runs on top of X. So your computer 'is' running on X. It is running KDE, which runs on X, so you would still use startx.

EDIT: I didnt explain that very well, did I...

Basically, all Linux systems running any GUI will be running X, so startx is still what you want

---

### Post by Delta62 on 2008-08-18
Okay, thanks for the clarification. What exactly does it mean then, that Kubuntu runs on K. Obviously this has nothing to do with the graphic system.

---

### Post by aktiwers on 2008-08-18
You can always use these too:

This one starts KDM
```
sudo /etc/init.d/kdm start 
```

This one restarts it
```
sudo /etc/init.d/kdm restart 
```

And this one stops it
```
sudo /etc/init.d/kdm stop
```

---

### Post by meanburrito920 on 2008-08-18
I'm sure there are plenty of essays on this if you just google it, but I'll give you a quick synopsis.

The modern Linux distro is seperated into multiple 'layers' of operation. From lowest to highest, they are:

1. Hardware (This technically is not part of the operating system...)

2. Kernel (This 'is' Linux -- the Kernel talks directly w/ the hardware)

3. The Shell (This is just a CLI to the kernel)

4. X Server (This talks to the kernel and the screen and tells the screen how to display, etc.)

5. The GUI (This would be KDE or GNOME, for example. This talks with X server and tells X server 'exactly' how it wants to do things. this includes how the windows should be drawn, how the menu bars act, etc.)

Hope that helps. Remember, GIYBF if you're looking for more info.

EDIT: Kubuntu runs KDE, whereas Ubuntu runs GNOME. There is no GUI called K.

---

