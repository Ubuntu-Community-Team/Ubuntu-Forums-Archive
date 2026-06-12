---
title: "Re-install Via USB Flash Drive Not Working.   Advice Requested."
date: 2014-04-05
forum: New to Ubuntu
---

### Post by TomBrooklyn on 2014-04-05
Ver: 12.04
Flash Drive: Sandisk Cruizer 4GB
Computer: Laptop Lenovo T400

Can anyone advise how I can reinstall Ubuntu 12.04 over corrupted version of Ubuntu 13.10.     It became corrupted when I tried to update Ubuntu while the computer was running on battery. 

I get the message: 
Remove disks or other media.   
Press any key to restart

I have tried all three USB ports with same result.

---

### Post by edeneen on 2014-04-05
need more info, how did you load the flash drive ?

---

### Post by philinux on 2014-04-05
If you can connect the laptop to wired internet.

boot it up and press the shift key after post to get the grub menu. Choose advanced. Then the second option which is recovery mode. At the menu choose root prompt.

then do this at the command prompt.

dpkg --configure -a

that might just fix 13.10 for you.

---

