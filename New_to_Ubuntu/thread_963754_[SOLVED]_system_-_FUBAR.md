---
title: "[SOLVED] system - FUBAR"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by adamogardner on 2008-10-30
All I did was restart my machine.

I have no title bar on my windows.  alt+f1 doesn't pull my menu.  Panels retract when I'm in panel's menu.  I have to open file > close to close windows.  My alt button doesn't seem to work at all.  ok looks like compiz is dead, I have no animations or water effects. I only have one workspace!  .

How did this happen?  How can I fix it?

---

### Post by LowSky on 2008-10-30
Alt+F2

type

compiz --replace

---

### Post by adamogardner on 2008-10-30
alt doesn't work,  I'm looking for that application in my menu.  what's it called?

---

### Post by LowSky on 2008-10-30
Terminal...LOL

---

### Post by adamogardner on 2008-10-30
ok so that widget at alt f2 is essentially a terminal?  fine.  I have to close my browser.  brb

---

### Post by adamogardner on 2008-10-30
The last part shows an error of some sort.  Compiz settings seem to work now though.  But what is it saying?

adamogardner@CRONUS:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0427 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

I don't completely get it.

---

