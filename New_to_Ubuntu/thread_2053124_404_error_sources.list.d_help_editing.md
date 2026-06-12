---
title: "404 error sources.list.d help editing"
date: 2012-09-04
forum: New to Ubuntu
---

### Post by fattyz on 2012-09-04
Hi i am trying to enable gnome shell extensions.  Ubuntu 12.04 gnome classic.  I am getting the following error trying to sudo apt-get update.

W: Failed to fetch [http://ppa.launchpad.net/awn-testing/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/awn-testing/ppa/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/awn-testing/ppa/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/awn-testing/ppa/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/awn-testing/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/awn-testing/ppa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

I have seen this before but forget how to fix it.  I can edit sources.list but I don't know what to change in the directory sources.list.d

Thanks

---

### Post by wojox on 2012-09-04
Remove the ppa's Ctrl+Alt+T:
```
gksudo software-properties-gtk
```

---

### Post by fattyz on 2012-09-04
Thx all set.:D

---

