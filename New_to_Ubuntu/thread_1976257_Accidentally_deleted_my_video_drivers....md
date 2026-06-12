---
title: "Accidentally deleted my video drivers..."
date: 2012-05-08
forum: New to Ubuntu
---

### Post by jamesbeat on 2012-05-08
I've been trying to fix some issues with choppy video on my Ubuntu 10.04LTS installation, and foolishly decided to delete and reinstall the propietory drivers for my graphics card the (the ATI R128 drivers).
I rebooted after deleting them, and my display says 'unsupported video resolution'!

Booting in failsafe graphics mode doesn't make a difference.
I tried booting into a root shell and installing the drivers from there, but it won't connect to the network, even through a physical connection via ethernet to my router.

What do I do?
Can I fix it from a liveCD session or something?

Edit: I forgot to add that the drivers were not found in the 'hardware drivers' section, but in package manager, and were installed automatically when I installed Ubuntu.

---

### Post by Peter09 on 2012-05-09
try
 
```
sudo apt-get install fglrx
```
 
se if that installs the correct drivers.

---

