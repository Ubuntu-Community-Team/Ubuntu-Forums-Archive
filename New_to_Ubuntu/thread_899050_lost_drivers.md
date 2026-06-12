---
title: "lost drivers?"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by frenchsquared on 2008-08-23
my sound and wirelss just quite working on a gateway m6824

gordon@Gateway:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 94c8
gordon@Gateway:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:94c8 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz: 406: /usr/local/bin/compiz: not found

can you all help me find out why

---

### Post by talsemgeest on 2008-08-24
Install envy, it is in the repositories. It will automate the installation of the very latest ati drivers, which should fix your problem.

---

### Post by frenchsquared on 2008-08-24
So for some reason when I was installing virtual box it create multiple ubuntu options on the grub boot loader. After some searching I was able to find the original boot option and everything is working. I then deleted all the other boot options from grub. 

I dont understand why virtualbox would change the boot menu or why my drivers would be lost.

---

