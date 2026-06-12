---
title: "Cannot install libgtk 2.0-dev via synaptic"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by Jengajam2 on 2008-09-13
When I tried to download and install it I got this error message:
```
libgtk2.0-dev:
 Depends: libcairo2-dev but it is not going to be installed
  Depends: libgtk2.0-0 (=2.12.9-3ubuntu2) but 2.12.9-3ubuntu4 is to be installed
 Depends: libpango1.0-dev but it is not going to be installed
```
Any help will be appreciated

---

### Post by ChanServ on 2008-09-13
have you tried installing libpango1.0-dev and libcairo2-dev first? and then installing libgtk 2.0-dev

---

### Post by Jengajam2 on 2008-09-13
> **ChanServ said:**
> have you tried installing libpango1.0-dev and libcairo2-dev first? and then installing libgtk 2.0-dev
I tried installing libcairo2 but i got this error:

```
libcairo2-dev:
  Depends: libcairo2 (=1.6.0-0ubuntu1) but 1.6.0-0ubuntu2 is to be installed

```

---

### Post by mc4man on 2008-09-13
Looks like your not updated to current hardy versions.  Go to system -> administration -> software sources and make sure 1st. 4 boxes are checked under the 'Ubuntu software' tab and the 1st 2 under the 'Updates' tab.

---

### Post by jemate18 on 2008-09-13
> **Jengajam2 said:**
> When I tried to download and install it I got this error message:
```
libgtk2.0-dev:
 Depends: libcairo2-dev but it is not going to be installed
  Depends: libgtk2.0-0 (=2.12.9-3ubuntu2) but 2.12.9-3ubuntu4 is to be installed
 Depends: libpango1.0-dev but it is not going to be installed
```
Any help will be appreciated

try updating your sources first
open terminal 
Applications -> Accessories ->Terminal

type```
sudo apt-get update
```

then try to install what you want

---

### Post by jemate18 on 2008-09-13
Have you solved the problem?

Is it working now?

---

### Post by Replika on 2008-10-11
> **mc4man said:**
> Looks like your not updated to current hardy versions.  Go to system -> administration -> software sources and make sure 1st. 4 boxes are checked under the 'Ubuntu software' tab and the 1st 2 under the 'Updates' tab.
Thanks.
The solution is check 'security', 'updates' and 'propose' in 'Updates' tab

---

