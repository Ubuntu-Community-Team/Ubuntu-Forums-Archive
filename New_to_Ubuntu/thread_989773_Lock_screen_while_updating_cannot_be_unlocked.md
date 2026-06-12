---
title: "Lock screen while updating cannot be unlocked"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by alfkh on 2008-11-22
I did a new ubuntu 8.10 install on a IBM Vista, /dev/sda3, with an existing Mint partition (mint is on /dev/sda1). As is customary for a new install, I did an update. Since Ubuntu updates take some time to complete, i decided to lock the screen so no one comes by to "screw-around" with it. When i returned, the screen could not be unlocked. My only alternative was to do a hard reset. i suspect that the filesystem was consequently damaged beyond repair.

When i tried reinstalling the system, it hung at the part where they asked for what is your keyboard localization. i suspect the system detected /dev/sda3 & was trying 2 recover it.

To resolve the problem, i ended up booting from the mint partition & deleting /dev/sda3. My question is, why didn't the unlock screen appear as stated in the documentation?

alvin
alfkh

---

### Post by jimmy the saint on 2008-11-22
There could be a lot of reasons for it, but finding them would require the system that had the error still being around to poke and prod.  It is possible that the system froze because of an error, or maybe it was still working when you restarted it.

---

