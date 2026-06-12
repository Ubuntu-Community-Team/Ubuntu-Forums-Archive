---
title: "vino-server installed but not starting"
date: 2012-10-12
forum: New to Ubuntu
---

### Post by nt 4 geeks on 2012-10-12
I have a remote ubuntu desktop on which I enabled the desktop sharing preferences to "Allow other users to view your desktop" and "Allow other users to control your Desktop". But when I am checking the status using /usr/lib/vino/vino-server it is showing
** (vino-server:25189): WARNING **: Command line `dbus-launch --autolaunch=54e6d79f4ef3600b1a1ed62500000008 --binary-syntax --close-stderr' exited with non-zero exit status 1: Autolaunch error: X11 initialization failed.\n
Cannot open display: 
Run 'vino-server --help' to see a full list of available command line options

I want to access ubuntu system using remote desktop both on another ubuntu and windows. What am I doing wrong?

Thanks in advance.

---

### Post by talha06 on 2012-10-23
having same problem while trying to access to a remote server.. any helps will be appreciated a lot.

---

### Post by dolphin194 on 2012-10-23
Have you checked this thread?
[http://ubuntuforums.org/showthread.php?p=8308582](http://ubuntuforums.org/showthread.php?p=8308582)

I personally don't use vino for my VNC sharing. Instead, I use x11vnc which only runs when you tell it to via SSH. You might want to look into that instead of vino, however I can help with vino if you still want to use it.

---

### Post by talha06 on 2012-10-23
> **dolphin194 said:**
> Have you checked this thread?
[http://ubuntuforums.org/showthread.php?p=8308582](http://ubuntuforums.org/showthread.php?p=8308582)

I personally don't use vino for my VNC sharing. Instead, I use x11vnc which only runs when you tell it to via SSH. You might want to look into that instead of vino, however I can help with vino if you still want to use it.
yeah I tried it and getting an error like this after xhost +:
```
No protocol specified
No protocol specified
xhost:  unable to open display ":0.0"
```

---

