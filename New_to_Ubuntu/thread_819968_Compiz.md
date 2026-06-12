---
title: "Compiz"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by ziffnabb on 2008-06-05
Hi all:
I have compiz & emerald installed.  If I try to enable some effects through the advanced desktop effects settings, nothing happens.  This is the output if I run compiz from the terminal.  How would I go about fixing the problem referred to in the last statement?

Thanks,
Ziffnabb


bruce@bruce:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0110 (rev b2) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

---

### Post by Joeb454 on 2008-06-05
Can you try ```
sudo apt-get install xserver-xgl
``` Does running ```
compiz --replace
``` work then?

---

