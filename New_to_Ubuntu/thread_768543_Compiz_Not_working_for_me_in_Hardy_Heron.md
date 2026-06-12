---
title: "Compiz Not working for me in Hardy Heron"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by SpaceMonk3y on 2008-04-26
Trying to do  compiz --replace and this is what i am getting in return.

Please help

> spacemonkey@spacemonkey-desktop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 03:00.0 0300: 10de:0193 (rev a2) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.




I am running a NVidia 8800 GTS Vid Card

---

### Post by chiefmanyrabbitguteat on 2008-06-06
This may be a bit late in coming, but do you have the Restricted Drivers enabled for your nVidia card?  Check System->Administration->Hardware Drivers.  You may have to enable this, and then reboot.

---

