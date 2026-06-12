---
title: "Update flashplayer problem"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by g9canon on 2008-11-01
I am a newbie to ubuntu and am using ubuntu 8.04. When I try to update the flashplayer using the update manager. I receive the following message.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Please advise what to do next. Thanks.:confused

---

### Post by kostkon on 2008-11-01
Open a terminal (*Applications -> Accessories -> Terminal*) and then give the following
```
sudo dpkg --configure -a
```
it will ask for a password, give yours.

This will fix your problem. After doing this, try to apply your updates again.

---

### Post by g9canon on 2008-11-01
Kostkon,

Your instructions have resolved the problem. On hindsight, I had tried typing into the terminal issuing instructions to correct the problem myself, but being the first time ever using the terminal, I was too ignorant to provide necessary spaces separating the various parts and therefore my attempt failed.

Thank you.

---

