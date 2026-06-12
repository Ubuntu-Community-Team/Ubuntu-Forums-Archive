---
title: "Trouble installing updates"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by scuminex on 2008-05-14
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Im not too familiar with "superuser privilege", but I need to be in order to solve this matter, according to my error pop ups. 
Any help on this would be greatly appreciated.

---

### Post by drs305 on 2008-05-14
> **scuminex said:**
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Im not too familiar with "superuser privilege", but I need to be in order to solve this matter, according to my error pop ups. 
Any help on this would be greatly appreciated.

You can gain superuser privileges temporarily with the 'sudo' command. Open a terminal and run:
```
sudo dpkg --configure -a
```
Type your password (you won't see it as you type) and Enter

---

### Post by SunnyRabbiera on 2008-05-14
Yeh this is a common issue, but easy to resolve nonetheless.

---

### Post by scuminex on 2008-05-14
Thanks friends. Like so many others, Ive realized, Im brand new to linux, but love it already. Thank you again.

---

