---
title: "Kde on ubuntu"
date: 2011-11-23
forum: New to Ubuntu
---

### Post by druid696 on 2011-11-23
I installed KDE on ubuntu and looking to get rid of it. How would I do that?

---

### Post by MG&amp;TL on 2011-11-23
I'm not sure if it still works, but this looks as if it should do the trick. [http://www.psychocats.net/ubuntu/puregnome]("http://www.psychocats.net/ubuntu/puregnome")

---

### Post by lolpenguin on 2011-11-24
```
sudo apt-get remove kubuntu-desktop
```
This removes ALL KDE components.

---

### Post by mutley89 on 2011-11-24
> **lolpenguin said:**
> ```
sudo apt-get remove kubuntu-desktop
```This removes ALL KDE components.

This won't work, as kubuntu desktop is a metapackage and doesn't actually contain anything, it just has a load of dependencies listed, which causes apt to drag in all the parts of kubuntu.  Removing it still leaves all the component parts.

---

### Post by ubume2 on 2011-11-24
> **MG&TL said:**
> I'm not sure if it still works, but this looks as if it should do the trick. [http://www.psychocats.net/ubuntu/puregnome]("http://www.psychocats.net/ubuntu/puregnome")

ditto

Also refer to these:

[https://help.ubuntu.com/community/InstallingKDE](https://help.ubuntu.com/community/InstallingKDE)

[http://packages.ubuntu.com/oneiric/kde/kde-full](http://packages.ubuntu.com/oneiric/kde/kde-full)

---

### Post by shymega on 2011-11-24
I would agree with MG&TL's answer.

Hope it gets sorted out.

shymega

---

