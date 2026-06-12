---
title: "[SOLVED] Lost Compiz effects but NVidia driver installed."
date: 2008-06-15
forum: New to Ubuntu
---

### Post by philinux on 2008-06-15
Nvidia-settings works fine. Ran Appearance from terminal, here's the output. 
```
gnome-appearance-properties %F
/usr/share/themes/Blubuntu/gtk-2.0/gtkrc:169: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.

(gnome-appearance-properties:6121): Gtk-WARNING **: Theme directory 1256x256/apps of theme crystal_project has no size field

WARNING: modinfo for module nvidia_new failed: modinfo: could not find module nvidia_new

WARNING: modinfo for module nvidia_legacy failed: modinfo: could not find module nvidia_legacy

WARNING: modinfo for module fglrx failed: modinfo: could not find module fglrx

There is no available graphics driver for your system which supports the composite extension.
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0402 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
```

---

### Post by aktiwers on 2008-06-15
Have you tried reinstalling the nvidia drivers? Seams like it can't find your drivers?
How much do you "score" in ```
glxgears
```? And what is the output of```
glxinfo
```?

---

### Post by sdennie on 2008-06-15
Are you running custom installed drivers from the nvidia website?  If so, some updates can overwrite parts of the nvidia installation and cause compiz to stop working (this usually manifests as not having window borders or not being able to start compiz at all).

Edit:
The fix is to simply reinstall the drivers.

---

### Post by Happy_Man on 2008-06-15
Apparently this has something to do with the recent X.Org update. Some people have reported success reinstalling the drivers. Try that and see if it helps.

---

### Post by philinux on 2008-06-15
Had to uninstall and purge then reinstall driver.

---

### Post by shifty_powers on 2008-06-15
oooooh, so that's what screwed up my effects and resolution :D

i fixed it exactly the same way as phil, with some help form envy, cos i'm lazy ;)

but nice to know why....

---

