---
title: "Auto-install dependencies?"
date: 2005-02-26
forum: Repositories &amp; Backports
---

### Post by SimonTheMime on 2005-02-26
Hm, I'm new to debian-based distros, and the closest thing before Ubuntu to an apt-get experience I've had is 'yum'. So is there a way on apt-get, like yum, to auto-install all dependencies? Everytime I try, it stops at failed dependencies, tells me it won't install them.

Thanks in advance,
Simon

Edit: And yes, I have the proper repositories checked.
Edit#2: Dammit, the KDE package (which is the one I want installed) said 'Does not include depends for development files. Can anybody tell me what development files I need, instead of spending the next 2hours gathering individual files to satisify the dependency hell going on here? *edits title*

---

### Post by RdChawda on 2009-04-15
After you fail to install the application, you can use:
"apt-get -f install"

This will automatically install all the dependencies, and also the program that you wanted to install

---

### Post by notgzus on 2012-03-07
=D> Perfect!

---

### Post by nuk28 on 2013-02-02
You can also try apt-get build-dep [package_name], for example: 
```
sudo apt-get build-dep banshee
```

---

