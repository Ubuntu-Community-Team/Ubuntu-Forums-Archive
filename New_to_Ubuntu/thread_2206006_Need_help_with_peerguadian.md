---
title: "Need help with peerguadian"
date: 2014-02-16
forum: New to Ubuntu
---

### Post by greg35 on 2014-02-16
So far, I have installed Ubuntu 13.10, and also got Chrome running. Now, though, I have hit a roadblock: how to get peerguardian running, which I already tried. I got it installed, but I couldn't access the web afterwards, period. I tried unblocking everything, but the result was the same, except that I was given an error message when I pressed apply. The error message said something about not being able to use gksu(do) or ksu(do). I tried changing the file in options, but I had no idea what I was doing, and so I still was where I had begun: unable to connect to the internet, and therefore unable to look up solutions. I tried telling it to stop, to close, even deleting it. Nothing worked. I did some brief research on my phone, and I couldn't find a solution. After much poking around, I chose to re-install Ubuntu 13.10, and while doing so delete the previous installation. This solved the issue for the browser not working, though I need help to get it working alongside peerguardian. Remember: I need simple, clear instructions.                                                                                                                                                                                                                                                                Thank you!  *greg35*

---

### Post by Vladlenin5000 on 2014-02-17
I don't use it but...
Clearly you can't/shouldn't run it as a normal user because in order to make such deep changes in the network configuration the program requires privileges, hence the error message. You need to run it like ```
gksudo pglgui
```

---

### Post by greg35 on 2014-02-17
I know there's more to it than that, but I don't know what else....

---

### Post by jre on 2014-05-20
pglgui requires root privileges for some commands. The helper program for this is configurable in pglgui (Options- Settings - Sudo front-end).In Gnome environments I recommend to use "/usr/bin/gksu" there.

No need to start the whole pglgui application with gksudo (although that might work, too)

---

