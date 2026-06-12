---
title: "Thurderbird error lockout"
date: 2012-05-09
forum: New to Ubuntu
---

### Post by bwallum on 2012-05-09
Thunderbird threw an error today 'Mozilla Error Reporter' window popped up and said TB had crashed, quit or restart.

Everytime I try to restart TB it throws the error window effectively locking me out of my email.

How do i overcome this please?

---

### Post by zombifier25 on 2012-05-09
Try starting Thunderbird in safe mode:
```
thunderbird -safe-mode
```

---

### Post by iMurshaq on 2012-05-09
If zombifier's solution dosen't work, try purging thunderbird and reinstalling

---

### Post by bwallum on 2012-05-09
> **zombifier25 said:**
> Try starting Thunderbird in safe mode:
```
thunderbird -safe-mode
```

Thanks zombi, that got me running again. The problem was the EDS manager add-on. Once this was disabled I could launch Thunderbird normally.

Many thanks again

---

