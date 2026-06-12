---
title: "Xubuntu System Beep"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by ryanparrish on 2008-07-20
I know how to get rid of the system beep in GNOME cant figure it out in XFCE I hate it when I back space to much and BEEEP and how do I fix sleep issues as well ? When I put the computer to sleep on resume it throws an error

---

### Post by jimmy the saint on 2008-07-20
i dont know about the suspend.  A commone issue with suspend is that gnome-screensaver is not running by default.  gnome-power-manager relies on it to function.  check out this thread [http://ubuntuforums.org/showthread.php?t=854557](http://ubuntuforums.org/showthread.php?t=854557)

as for the system beep.  enter "xfce4-mixer" into the terminal and turn down the system beep slider.  That should mute it.

---

### Post by ibuclaw on 2008-07-20
```
sudo rmmod pcspkr
```
That will remove the system beep for your current session.

To make it permanent:
```
sudo gedit /etc/modprobe.d/blacklist
```
And put at the bottom of the file
```
blacklist pcspkr
```

Regards
Iain

---

