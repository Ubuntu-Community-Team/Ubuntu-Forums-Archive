---
title: "synaptic thinks its going!"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by jon zendatta on 2008-05-09
hell0
just did a fresh install now gathering up some programs..problem being in the following output, as i do not have synaptic or add/remove running..any ideas how to kill this :KS

---

### Post by jon zendatta on 2008-05-09
ne@one-laptop:~$ sudo apt-get install googleearth
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  googleearth-data
The following NEW packages will be installed:
  googleearth googleearth-data
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

---

### Post by Six_Digits on 2008-05-09
Try a restart? Only solution I can think of, as you said synaptic and add/remove aren't open.

---

### Post by canadianwriterman on 2008-05-09
I have had a problem that may be related. The package manager icon stays on sometimes in the top panel. If that icon is showing on your desktop, try clicking on it. When the update manager opens, click on the refresh (or reload, I can't remember offhand) button. Once it has reloaded, then the lock on the package manager should go away.

---

