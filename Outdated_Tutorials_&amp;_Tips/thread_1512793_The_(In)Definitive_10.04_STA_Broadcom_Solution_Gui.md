---
title: "The (In)Definitive 10.04 STA Broadcom Solution Guide"
date: 2010-06-18
forum: Outdated Tutorials &amp; Tips
---

### Post by Sepero on 2010-06-18
After system upgrade on Dell inspiron 1545 with Update Manager, the wifi driver breaks and stops working. The OSS b43 driver does not work on this system at all.

I solved this problem for a friend on their laptop. No compiling required. I hope this helps.


1. Add the LiveCD as a repository and Uncheck ALL other repositories.
System> Administration> Software Sources

2. Update software sources. This can be done when you close the Software Sources window, or by using Synaptic.
System> Administration> Synaptic Package Manager> Reload (button)

3. Use Synaptic to Remove bad packages if they are installed.
System> Administration> Synaptic Package Manager> Search (button)
* bcmwl-kernel-source
* b43-fwcutter
* linux-image-2.6.32-22-generic (any linux-image 2.6.32-22 or greater)

4. Use Synaptic to Lock the kernel package linux-image-2.6.32-21-generic, and lock the package linux-headers-generic to version 2.6.32-21.32. (This will prevent the problem from occurring again with future upgrades).
System> Administration> Synaptic Package Manager> Package (menu)> Lock Version

5. Reboot (restart)

6. Install the wifi driver.
System> Administration> Hardware Drivers

7. Reboot (restart)

8. Remove the LiveCD as a repository, and Recheck all the repositories that were unchecked in step #1.
System> Administration> Software Sources



Credits to:
[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

