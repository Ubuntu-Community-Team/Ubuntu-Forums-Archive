---
title: "Lubuntu automatically restart several times before normal work"
date: 2020-01-21
forum: New to Ubuntu
---

### Post by receptor2 on 2020-01-21
I've installed Lubuntu on new SSD and it works fine at first. 
But after a month of use it autorestarts multiple times (10-20) when I enable my PC.
It can restart on login screen or after that.

**lsb_release -a**:
```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.3 LTS
Release:    18.04
Codename:   bionic
```

Preferences -> **Disks** -> SMART Data & Self Tests 
says that **Disk is OK**:
[ATTACH=CONFIG]284838[/ATTACH]

How to find a reason of the problem and fix it? 
I'll add all necessary information that will be required to a thread.
PS: Sorry for my bad English and if I post to a wrong forum category.

---

### Post by stoogiebuncho on 2020-01-23
Auto restarts are often caused by overheating.  The SMART test results you posted have a temperature reading of 99 C / 210 F, which is really hot.  Are you sure your fans and other cooling elements are functioning properly?

---

### Post by guiverc on 2020-01-23
I had a laptop fan that was failing (it wasn't easily obvious; it maybe was a little quiet but who notices that!??!) and it was only the thinkpad turning off that eventually made me take notice.

I loaded sensors and had a conky script run on screen (refreshing every 2 secs) displaying the cpu temperature.  Many cpu's start to throttle speed once temperature hits a certain point, but 100oC was my laptops shutdown threshold.  I suspect @[COLOR=#000000]stoogiebuncho[/COLOR] has detected your issue  (the 99oC was probably just before one of the shutdowns).

---

