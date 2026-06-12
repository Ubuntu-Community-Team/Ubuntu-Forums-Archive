---
title: "DPKG configure -a freezes"
date: 2018-06-25
forum: New to Ubuntu
---

### Post by rpgmorpheus on 2018-06-25
Hi everyone.

I can usually deal with linux issues, but this one I can't figure out.

Basically I tried to reinstall virtual box on Ubuntu 18, as the one installed through the website no longer worked.
(Gave me a not supported kernel error of some kind, can't remember) 

This is why I tried to install virtual box by installing virtualbox-dkms, as some posts suggested.

Something must've gone wrong however, as it never finished, and always stops at the same exact operation:

> 
Setting up virtualbox-dkms (5.2.10-dfsg-6) ...
Removing old virtualbox-5.2.10 DKMS files...


-------- Uninstall Beginning --------
Module:  virtualbox
Version: 5.2.10
Kernel:  4.15.0-22-generic (x86_64)
-------------------------------------


Status: This module version was INACTIVE for this kernel.
depmod...


DKMS: uninstall completed.


------------------------------
Deleting module version: 5.2.10
completely from the DKMS tree.
------------------------------
Done.
Loading new virtualbox-5.2.10 DKMS files...
Building for 4.15.0-22-generic
Building initial module for 4.15.0-22-generic


Nothing happens after this, and my package manager is locked, so I can no longer install / update packages.
After a restart, whatever I try to do it always tries to do the above, and just freezes.

Running the following does the same as well:

> 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.


I've completely ran out of ideas now, and I don't know where to look for logs.

---

### Post by Xian on 2018-06-26
This forum post might be of some help:

[https://ubuntuforums.org/showthread.php?t=2393436](https://ubuntuforums.org/showthread.php?t=2393436)

---

### Post by rpgmorpheus on 2018-06-26
Yep, the following instructions worked out:
[https://ubuntuforums.org/showthread.php?t=2393436&p=13773023#post13773023](https://ubuntuforums.org/showthread.php?t=2393436&p=13773023#post13773023)

Thanks!

---

