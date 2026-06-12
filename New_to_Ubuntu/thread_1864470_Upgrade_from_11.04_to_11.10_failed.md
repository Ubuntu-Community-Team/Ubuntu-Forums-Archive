---
title: "Upgrade from 11.04 to 11.10 failed"
date: 2011-10-19
forum: New to Ubuntu
---

### Post by ENigma885 on 2011-10-19
I started an upgrade from Natty to Oneiric and everything seemed to be ok; no errors appeared. Restarted the system, but I cannot get to the login screen anymore.
The boot messages stop with
```
mountall: Plymouth command failed
mountall: Disconnected from Plymouth
```

**_##What I did in a try to find a solution_**
**1-** Tried to to login using recovery mode (The system wasn't mounted in read/write mode. So, I had to ```
mount -o rw,remount /
```
**2-** Run update and upgrade, all packages were installed but still the same behavior is persistent.
**3-** run ```
sudo update-alternatives --config default.plymouth
``` to change Plymouth's theme (I have disabled the splash screen anyway but was a hopeless try)
**4-** tried to reconfigure Lightdm 
```
sudo dpkg-reconfigure lightdm
```
**5-** Tried to launch Lightdm by ```
sudo lightdm
``` from the root shell, the system turned into a blank black screen directly.

---

