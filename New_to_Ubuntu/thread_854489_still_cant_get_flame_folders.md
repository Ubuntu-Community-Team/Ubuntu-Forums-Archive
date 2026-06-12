---
title: "still cant get flame folders"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by westentertainer on 2008-07-09
hello i have tried every thing to get burning folders like i had in 7.04 cant seem to get it to work in 8.04 can anyone take the time to give me step by step instructions  thanks a lot

---

### Post by LowSky on 2008-07-09
burning folders? Do you mean with Beryl/Compiz? OR Like burning folders to a CD?

---

### Post by westentertainer on 2008-07-09
sorry compiz

---

### Post by billgoldberg on 2008-07-09
Open up the advanced desktop effects manager.

In the "animations" sub menu, select the "close effect" tab.

Edit the current string, and pick "burn".

That should do it.

---

### Post by westentertainer on 2008-07-09
i tried it still wont burn

---

### Post by LowSky on 2008-07-09
go to terminal type

compiz --replace

then try

---

### Post by westentertainer on 2008-07-09
this is what i gettony@tony-desktop:~$ compiz -replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0326 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Warn: Unknown option '-replace'

/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

---

### Post by billgoldberg on 2008-07-09
> **westentertainer said:**
> this is what i gettony@tony-desktop:~$ compiz -replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0326 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Warn: Unknown option '-replace'

/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

it --replace (two -)

But it seems xgl isn't installed.

Does compiz fusion even works?

---

### Post by westentertainer on 2008-07-09
yes i think  compiz works i have wobbly windows  what can i do

---

