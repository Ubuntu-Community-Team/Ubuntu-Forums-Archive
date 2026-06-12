---
title: "Cen't get monitor to work"
date: 2011-12-09
forum: New to Ubuntu
---

### Post by morphv on 2011-12-09
Hi all,
 
this is my first post and I hope this is the right place.
I'm not so expert on linux.
I've been struggling in order to get to work my monitor on Acer Aspire One 0715h ZA3.
I correctly downloaded and installed Lubuntu on it, but while it is booting, the startup process ends just before X window starts.
I've tried many solutions found on the web but I'm still working on it since no one helped me.
I tried to modify Xorg monitor configuration file (10-monitor.conf under /usr/share/X11/xorg.conf.d directory) but nothing happened.
The error is "Number of created screens does not match number of detected devices".
I didn't install any proprietary driver.
The only thing I suppose is that the error happens because of the "double" monitor the netbook has (one is the video card and the other one is the VGA on output). 
 
Thansk in advance.
 
 
P.S. excuse for my english

---

### Post by marinara on 2011-12-09
did you see this page: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/#Driver_overview](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/#Driver_overview)

i've heard the new OpenSUSE works well on laptops with 2 video cards.  If you get stuck, you might try it.

---

### Post by Diametric on 2011-12-09
But you do get use of a tty session - you just cannot start an x window session?

---

### Post by morphv on 2011-12-09
I can work on it through a tty session by pressing Ctrl+Alt+F1 at boot.
I also activated sshd so that I can configure it better from my Mac.
I can't start X window session; for example xrandr says "Can't open display".

---

### Post by Diametric on 2011-12-09
Yikes.  I might try and investigate the dual monitor card issue and see where that leads.  Good luck!

---

### Post by morphv on 2011-12-09
> **marinara said:**
> did you see this page: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/#Driver_overview](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/#Driver_overview)
 
i've heard the new OpenSUSE works well on laptops with 2 video cards. If you get stuck, you might try it.
 
Yes, I tried it but unfortunately I wasn't able to succeed. 
Sometimes I wonder if I'm able to operate. :(

---

