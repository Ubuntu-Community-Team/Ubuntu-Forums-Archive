---
title: "[SOLVED] errors while updating packages"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by crazypenguin2008 on 2008-09-23
i noticed i had 45 updates available before i left for work this morning. i set it to install them and i left. my wife went to use the pc to pay some bills and this error came up. she copied it to a email and sent me. 

what does it mean and how do i fix it?? 



E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

---

### Post by jemate18 on 2008-09-23
> **crazypenguin2008 said:**
> i noticed i had 45 updates available before i left for work this morning. i set it to install them and i left. my wife went to use the pc to pay some bills and this error came up. she copied it to a email and sent me. 

what does it mean and how do i fix it?? 



E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

open terminal
> Applications -> Accessories - > Terminal

type
```
sudo apt-get update
``` then your password and hit enter

type
```
sudo apt-get upgrade
```then your password and hit enter

---

### Post by sharks on 2008-09-23
maybe at that time, you maybe having two application installers opened(synaptic and add/remove programs)

---

