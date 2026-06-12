---
title: "Uninstalling Opera"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by awseft on 2008-04-29
I installed it to test a few things. 

It was quick but I still want to uninstall it. It isn't in Add/Remove programs. I want to leave as little behind of it as possible. 

Thanks!

---

### Post by encompass on 2008-04-29
How did you install it?
That's will help figure out what to do next.

---

### Post by awseft on 2008-04-29
> **encompass said:**
> How did you install it?
That's will help figure out what to do next.

I went to their website. Clicked download. It just opened the file and it automatically unpacked and installed.

---

### Post by encompass on 2008-04-29
Odds are you installed the DEB thank goodness..
```
sudo apt-get remove --purge opera
```
if that doesn't remove it... try the same command but press tab a few times at the end and it should autocomplete what ever it should be.

---

### Post by awseft on 2008-04-29
> **encompass said:**
> Odds are you installed the DEB thank goodness..
```
sudo apt-get remove --purge opera
```
if that doesn't remove it... try the same command but press tab a few times at the end and it should autocomplete what ever it should be.

THANKS!

---

