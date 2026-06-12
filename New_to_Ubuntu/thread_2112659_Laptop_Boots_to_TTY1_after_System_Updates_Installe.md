---
title: "Laptop Boots to TTY1 after System Updates Installed"
date: 2013-02-05
forum: New to Ubuntu
---

### Post by ajdrew06 on 2013-02-05
Hi All,

My laptop has been running 12.04 for some time now. I installed the recommended system updates that popped up yesterday, and now it boots into TTY1. I read I should try typing "startx". I get about 25 lines that say [OK], but then my laptop freezes. 

I don't remember exactly what updates were installed yesterday. Is there a log to find out which were installed? Is there a way to uninstall those particular updates to "rollback" my system?

Thanks!
-Drew

---

### Post by ibjsb4 on 2013-02-05
When in TTY try:

Ctrl + Alt + F7

---

### Post by ajdrew06 on 2013-02-05
I've tried that. It spits out a bunch of lines... nothing to indicate any errors that I saw at first glance, but I'm not really sure what I should be looking for. The system still hangs after spitting out a bunch of info.

---

### Post by ibjsb4 on 2013-02-05
Can you boot to recovery mode?

And check to see if your video driver has been replaced.

---

### Post by ajdrew06 on 2013-02-05
I tried to boot in recovery mode. I wasn't sure what mode to try. I tried to boot in the graphics failsafe mode (or whatever it was called) & it hung. 

I'm not familiar with many of the boot options, so you will have to be more detailed, sorry.

---

### Post by cap10Ibraim on 2013-02-05
```

vi /var/log/apt/history.log

```
mostly update of the kernel or graphics card module 
Can you spot suspects from the log file ?

---

### Post by ajdrew06 on 2013-02-05
This is the last set of updates that I installed...

Start-Date: 2013-02-04  20:41:42
Commandline: apt-get upgrade
Upgrade: libnih-dbus1:i386 (1.0.3-4ubuntu9, 1.0.3-4ubuntu9.1), lightdm:i386 (1.2.1-0ubuntu1.1, 1.2.3-0ubuntu1), xserver-common:i386 (1.11.4-0ubuntu10.8, 1.11.4-0ubuntu10.11), xserver-xorg-core:i386 (1.11.4-0ubuntu10.8, 1.11.4-0ubuntu10.11), liblightdm-gobject-1-0:i386 (1.2.1-0ubuntu1.1, 1.2.3-0ubuntu1), gstreamer0.10-plugins-bad:i386 (0.10.22.3-2ubuntu2.1, 0.10.22.3-2ubuntu2.2), libgstreamer-plugins-bad0.10-0:i386 (0.10.22.3-2ubuntu2.1, 0.10.22.3-2ubuntu2.2), libnih1:i386 (1.0.3-4ubuntu9, 1.0.3-4ubuntu9.1)
End-Date: 2013-02-04  20:42:11

Does this information help?

---

### Post by cap10Ibraim on 2013-02-06
I would try to reinstall xorg-server and if that didn't work downgrade it

---

