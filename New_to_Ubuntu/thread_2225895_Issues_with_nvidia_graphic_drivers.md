---
title: "Issues with nvidia graphic drivers"
date: 2014-05-24
forum: New to Ubuntu
---

### Post by bruno17 on 2014-05-24
Hello all! I'm a beginner in linux and I'm really enjoying the system, now I don't want back to Windows anymore. 

I have a Geforce 6150se nForce 430 (yes, very poor card) and unfortunately I'm having issues with nvidia drivers, firstly the current version (304.117) made my system with something like blurred letters, really ugly. So I tried the version 173 and the blurred letters bug was fixed but the resolution cannot be higher than 1024x768, my monitor is a 1366x768 Samsung B1930. What can be done? For now I'm using nouveau drivers but they are very weak.

Thank you and sorry for my English.

PS: My Xubuntu is 14.04

---

### Post by hyperreal on 2014-05-24
Have you installed the recommend driver listed on the Driver Install utility?  

In any case, change to another virtual terminal (CTRL+ALT+F2), login and run "sudo nvidia-xconfig".  Reboot, and see if that fixes your resolution.

Also, can you post your /var/log/Xorg.0.log?

---

### Post by bruno17 on 2014-05-24
> **hyperreal said:**
> Have you installed the recommend driver listed on the Driver Install utility?  

In any case, change to another virtual terminal (CTRL+ALT+F2), login and run "sudo nvidia-xconfig".  Reboot, and see if that fixes your resolution.

Also, can you post your /var/log/Xorg.0.log?

Hello! Thanks for the help.

Where can I see the recommended driver? I'm using Xubuntu.

---

### Post by hyperreal on 2014-05-24
Look in the Applications Menu > Settings.  There should be an option for installing drivers.  If there isn't, then install the package 'jockey-gtk'.  sudo apt-get install jockey-gtk.

---

