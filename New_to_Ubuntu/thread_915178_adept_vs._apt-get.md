---
title: "adept vs. apt-get"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by buntu_hugenewbie11 on 2008-09-09
I recently installed Hardy on a new computer and I found that apt-get upgrade doesn't seem to actually upgrade as packages are kept back all the time.
But the adept package manager seems to always signal that certain packages are upgradable.

Is it bad to use both adept package manager and apt-get?

Is one preferable over the other?

---

### Post by Titan8990 on 2008-09-09
You are just giving apt-get the wrong command. Adept updater uses aptitude. The command you are looking for is this:

sudo apt-get dist-upgrade


Dist-upgrade also installs dependencies needed up upgrading.

---

### Post by nickgaydos on 2008-09-09
I wouldn't see why it would be bad to run both on the same machine, I do cause of KDE...I just perfer apt-get over adept because I am used to apt-get.

---

### Post by skymera on 2008-09-09
sudo aptitude full-upgrade

---

### Post by LowSky on 2008-09-09
> **buntu_hugenewbie11 said:**
> I I found that apt-get upgrade doesn't seem to actually upgrade as packages are kept back all the time.
  
dont forget sudo, nothing will happen without it
```
Sudo apt-get upgrade
```

---

### Post by buntu_hugenewbie11 on 2008-09-09
No I didn't mean a distribution upgrade. Just package upgrades. But on that note is there a difference between aptitude and apt?

---

