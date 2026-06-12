---
title: "Problem running Emerald and Compiz Fusion"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by wariskampar on 2008-05-24
I installed Emerald and Compiz Fusion from Synaptic. But when open Emerald, I dont see any theme. I'm also confuse over Windows Management; Metacity or Emerald. Read in one thread to enter below code in terminal. But this is what I get:

aznan@aznan-laptop:~$ compiz --replace -c emerald
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2592 (rev 04) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Warn: Unknown option '-c'

/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'emerald'
/usr/bin/compiz.real (core) - Warn: Plugin 'core' already active
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

Could someone assist me setting up Emerald and Compiz Fusion.

---

### Post by markbuntu on 2008-05-24
Look in the Multimedia and Video Forum there is a lot of discussion about this particular problem you are experiencing. You are using the restricted ATI driver yes?

---

