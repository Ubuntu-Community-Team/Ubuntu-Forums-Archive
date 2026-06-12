---
title: "[SOLVED] how to edit xorg.conf?"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by jorj82 on 2008-10-31
This probably sounds like a dumb question, but anyways, how can I open this file with permission to write?  I'm trying to change my color depth to 16 because onboard graphics suck.  I've read plenty of posts that explain how to do it, but I can't do it.  When I use the terminal for dpkg-reconfigure xserver-xorg, it only reconfigures the keyboard and nothing else.  When I try to edit xorg.conf manually, it won't let me save the file.  Long story short, I know what to do, I just can't do it.  Help?

---

### Post by drs305 on 2008-10-31
I won't make a judgment on your decision to manually edit xorg.conf, but to edit it you must assume administrative power to alter a system file. The following commands will open the file after saving it:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
gksudo gedit /etc/X11/xorg.conf
```

---

