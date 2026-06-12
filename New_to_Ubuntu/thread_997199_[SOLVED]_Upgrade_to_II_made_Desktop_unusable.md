---
title: "[SOLVED] Upgrade to II made Desktop unusable"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by Tom Atkins on 2008-11-29
I Had two installs of HH on my system on separate disk drives. When I updated one to II it did not recognize my screen properly and the resolution is set so large I can not get to the bottom of a screen to check apply, etc. and the menu bar is on the right side. The screen should be PTS 17", 1280x1024, 75 HZ. I can get to the terminal. Is there a command I can use to fix this or do I have to do a clean install via the HH to II route as I only have the HH DVD I purchased several months age.

---

### Post by linux_tech on 2008-11-29
Resolution settings can be changed here-
 System > Preferences > screen resolution

xandr is a command that will change screen size
```
man xrandr
```
```
xrandr [-help]  [-display display] [-o orientation] [-q] [-v] [-s size]
```
ie ```
xrandr --output LVDS --mode 1024x768 
```
Always backup your configuration file 1st:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```


```
https://wiki.ubuntu.com/X/Config/Resolution
```

Resolution can also be set in xorg.conf

 HOWTO: change resolution/refresh rate in Xorg
```
http://ubuntuforums.org/showthread.php?t=83973
```

---

### Post by Tom Atkins on 2008-11-29
Thanks for the help. I was able to set my system video up properly. Just the way the default set it up the only thing I could access was the terminal.

Thanks again

---

