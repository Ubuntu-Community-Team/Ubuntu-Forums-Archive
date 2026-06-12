---
title: "I keep Losing my wireless"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by Foxfire on 2008-07-26
I followed this post  Installing BCM94311MCG wlan mini-PCI on 7.10 & 8.04 - Broadcom wifi on a HP dv9000

worked great but now when i restart i dont have wireless anymore

---

### Post by phidia on 2008-07-26
Is [this]("http://ubuntuforums.org/showthread.php?t=769990&highlight=BCM94311MCG") the thread you used to install/enable wireless?

Did you do this step? > Step 11

    Now we need to add ndiswrapper to the modules file
    Code:

    sudo gedit /etc/modules

    just add the following at the end of the file and save and close it.
    Code:

    ndiswrapper



Make sure ndiswrapper is in /etc/modules.

---

### Post by Tim Sharitt on 2008-07-26
You may also have to add 
```
blacklist b43
```
to /etc/modules.d/blacklist for 8.04

---

### Post by Foxfire on 2008-07-26
is this right

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
ndiswrapper


I put it at the end

---

