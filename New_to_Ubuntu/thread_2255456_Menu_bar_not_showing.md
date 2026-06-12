---
title: "Menu bar not showing"
date: 2014-12-05
forum: New to Ubuntu
---

### Post by Muhammad_Shahzad on 2014-12-05
I installed Ubuntu 13.04 on my 32bit system, but there are many issus.

1) Menu bar not showing
2) Some time my PC goes to hang out.
3) I'm unable to install any package like tint2

Run Commond:

        > sudo apt-get install tint2

I got error;
> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package tint2


---

### Post by veddox on 2014-12-05
Please note that 13.04 reached its end of life in January ([https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)) and is thus no longer supported update-wise. I suggest you download 14.04, the latest long-term release, or 14.10, the current short-term release.

---

### Post by eight.coffee.beans on 2014-12-05
Ubuntu 14.10 finds a package called tint2, so your fix is to install either Ubuntu 14.04 [LTS] or Ubuntu 14.10 and these issues shoud be fixed.

If you wish to upgrade your Ubuntu, you can do it by typing the following in your Terminal:
```
sudo do-release-upgrade
```

---

