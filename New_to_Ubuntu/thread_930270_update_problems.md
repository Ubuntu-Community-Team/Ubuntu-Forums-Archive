---
title: "update problems"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by jeff Odom on 2008-09-25
It said I had 119 updates available, but when I did the updates a few of them had errors because it could not collect from the "Ubuntu Security site".

---

### Post by drs305 on 2008-09-25
You could try another server - Synaptic, Settings, Respositories, Click on the 'Download from' window and select > other. Then select Best Server or select a specific server.

If you think your sources.list may be the problem, you should have a line similar to the following: 
```
deb http://security.ubuntu.com/ubuntu/ hardy-security restricted main universe multiverse

```
(You can view your sources.list file by typing: cat /etc/apt/sources.list

If your problem is preventing you from downloading the other updates, temporarily deselect the (hardy-security) box in the 'Updates' tab until you have finished updating the rest of your packages. Remember to reselect it.

---

### Post by pi.boy.travis on 2008-09-25
Can you post the output of:

sudo apt-get update?

---

### Post by jemate18 on 2008-09-25
please post your sources.list

> cat /etc/apt/sources.list

---

### Post by jemate18 on 2008-09-25
you have double posted your problem.......

> [http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326)

---

