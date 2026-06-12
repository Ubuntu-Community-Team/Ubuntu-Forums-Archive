---
title: "[SOLVED] Cannot enable visual effects"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by midgetwithamatch on 2008-11-18
I am using ATI x850 Pro and used the following website to set it up. [https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")
I just upgraded my desktop from 8.04 to 8.10 last night and now the visual effects will not start via System->Preferences->Appearance. I ran it from terminal and got this  
```
There is no available graphics driver for your system which supports the composite extension, or the current one already supports it.
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 
Window manager warning: 0 stored in GConf key /desktop/gnome/peripherals/mouse/cursor_size is out of range 1 to 128
Window manager warning: 0 stored in GConf key /desktop/gnome/peripherals/mouse/cursor_size is out of range 1 to 128

```

Also ran these...
```
jeromy@ShapeshiftingContortionist:~$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa Project
jeromy@ShapeshiftingContortionist:~$ glxinfo | grep "direct rendering"
direct rendering: Yes

```

xorg.conf is attached as xorg.txt.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Edit: I fixed the problem by doing a fresh install by way of the live / install CD. Must have something to do with the upgrade itself.

---

### Post by gychang on 2008-11-21
I also can not enable visual effects on 8.1.

how do I go about checking and fixing this problem?

thanks in advance.

gychang

---

### Post by Bölvaður on 2008-11-21
what videocard do you have?
is it powerful enough to support compiz?

---

### Post by gychang on 2008-11-21
> **Bölvaður said:**
> what videocard do you have?
is it powerful enough to support compiz?

is this the correct information?

VT8375 [ProSavage8 KM266/KL266]

gychang

---

