---
title: "[SOLVED] Booting my 2nd harddrive with Linux"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by dixiedownunder on 2008-10-11
My friend gave me a 40 GB harddrive with Linux installed.  I've installed it as a 2nd harddrive and I can boot it if I change the boot order in the BIOS.  The problem is that I can't read the screen once it happens.  I guess I don't have the right drivers for my monitor or my settings may be wrong.  I can tell it's some kind of login screen and I can make out the words 'UBUNTU'.

Thanks for your help.  I'm a n00b, but I'm pretty excited about it.

---

### Post by linux_lover69 on 2008-10-11
It would be easier to reinstall Ubuntu on your new hard drive. Because the video settings is set for the other guys computer. You might be able to go into safe mode and go to fix x server and that might fix the graphics problem.

---

### Post by bumanie on 2008-10-11
The above post is probably correct in that the OS has been configured for a different computer. You could try a couple of things before resorting to a reinstallation - they may or may not work. Firstly go to System --> Administration --> Hardware drivers and see if a graphics driver has been enabled, if not click the check box and a driver should download Assuming you have internet connection). You could also go to terminal and type > sudo xfixIt is the 'new' way to try to fix x-server in 8.04. As far as having to change bios to boot ubuntu, that indicates that grub needs reinstalling - but don't worry about that if you can't get the graphics right first. You may have to reinstall as during installation, your hardware is checked and appropriate drivers enabled, unless your computer is the same as your friend's, the correct drivers for your hardware may not be enabled.

---

### Post by dixiedownunder on 2008-10-11
Thanks guys.  I think I will just try to reinstall it.  It's not the latest version anyway and I think I want to run 64 bit just for the hell of it.

---

### Post by dixiedownunder on 2008-10-12
Reinstalling worked!

---

