---
title: "Nvidia driver problem"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by stunningman on 2008-10-08
my system was showing good resolution when i activated restricted driver from system>administration>hardware driver ,later i installed nvidia driver 173.14.12 my screen resolution is no more than 800*600.how to bring back my good previous resolution or is there any setting which can just work.





sys:intel quad @6600,2gb ram,320 harddisk,geforce 8500 gt

---

### Post by inxygnuu on 2008-10-08
what was your screen resolution before?

also try this:

System->prefrences->screen resolution

(note; **_don't set it extremely low, it could give you serious problems!_**)

---

### Post by stunningman on 2008-10-08
ya i tried that too.my earlier resolution was 1024*768 and i have option to set it higher. now when the ubuntu is booting it says low resolution.

---

### Post by stunningman on 2008-10-08
is the driver nvidia-linux-173.14.12 right for geforce 8500gt or is it fine.

---

### Post by phidia on 2008-10-08
> **stunningman said:**
> is the driver nvidia-linux-173.14.12 right for geforce 8500gt or is it fine.

You can probably use the latest driver with that card.
It sounds like you are installing the driver from the nvidia site.
There should be no harm in using the 177 driver.

---

### Post by pi.boy.travis on 2008-10-08
Have you tried Applications-Other-Screens and Graphics?  It is hidden by default.  Right click on the menu to get to the menu editor.

Hope this helps!

---

### Post by stunningman on 2008-10-08
ya i tried it but in vain nothing seems to work even the proprietary driver listed in system>administration>hardware driver. is empty. which earlier worked is missing.

---

### Post by knix on 2008-10-08
A. Diagnostics
1. Boot into recovery mode
2. Choose root from the menu if you get one.
3. Run "startx >> xerrors.txt"
4. Boot into something that works and post the contents of the file.

B. How to get the driver working (usually)
1. Make sure nvidia-glx-173 (if in intrepid) is installed, or the apropriate nvidia-glx-new packages for hardy.
2. Run "nvidia-xconfig" as root. Youl will need to edit your xorg.conf a little in intrepid.
3. If in intrepid, remove the "Files" Section from your /etc/X11/xorg.conf.
4. Reboot.
5. If you're in intrepid, you'll want to run "/etc/init.d/dkms_autoinstaller start" as root.
6. If it doesn't work, go to section A.

---

