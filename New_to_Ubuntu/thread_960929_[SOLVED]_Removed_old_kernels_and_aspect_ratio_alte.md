---
title: "[SOLVED] Removed old kernels and aspect ratio altered ??"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by Windy Peaks on 2008-10-27
Ladies and Gentlemen of the forum:

I was foolishly following the directions from a APC magazine and tried to remove some older kernels.
After searching "linux-image" through synaptic and clicking removal of the older kernels, then rebooting the computer. The monitor aspect settings were requested by the software, but I made the wrong selecting and now I'm stuck with what looks like 16:9 when I needed 3:4.
Any ideas on this one ???

Thanks in advance
Windy

---

### Post by nhasian on 2008-10-27
press CTL-ALT-F1 to get to a terminal.

then stop the graphical display manager with

```
sudo /etc/init.d/gdm stop (or kdm for KDE)
```

then to configure the display type:

```
sudo dpkg-reconfigure xserver-xorg
```

then finally to start the GDM again do:

```
sudo /etc/init.d/gdm start (or kdm for KDE)
```

---

