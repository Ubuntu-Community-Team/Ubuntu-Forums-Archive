---
title: "Install OSSEC in Ubuntu via APT"
date: 2018-08-22
forum: New to Ubuntu
---

### Post by dzonii on 2018-08-22
Hello everyone i got problem when i try to install OSSEC from [https://www.ossec.net/downloads.html](https://www.ossec.net/downloads.html)  through APT. I tried both manually and automatically,and none of them  works, when i tried i got this message "unable to correct problems you  have held broken packages ".Does anyone has idea how to solve this ??

---

### Post by TheFu on 2018-08-22
Manually installed .deb files can force other packages to be held - no upgrades allowed.  
The general solution is to avoid ever installing .deb files directly.  If you do, it is very common for APT dependency issues to come up in 3-6 months.  
The solution is to stay with packages from the core Canonical repos whenever possible.  Failing that, use a reputable PPA from a trusted source.

If you do install any packages manually from .deb files, be certain to keep track of them so you can manually remove them later to allow the system to be patched again.  By that point, it is probably time to find a newer version of the .deb file anyway.  This is the requirement for any manually installed .deb files.

If you want to avoid that, you can get the source files and manually install those without using the package manager. This will prevent the "APT Hell" dependency issue, but someone will still need to manually get the newest source and manually update the packages to retain a secure system.

IMHO.

---

### Post by dzonii on 2018-08-31
So how can install ossec from PPA ? when its only avaliable through deb ?

---

