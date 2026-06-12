---
title: "making a deb package of wxDownloader for Gutsy"
date: 2007-10-29
forum: Packaging and Compiling Programs
---

### Post by go_beep_yourself on 2007-10-29
How can I make a deb Ubuntu package of wxDownloader for Gutsy?

[http://dfast.sourceforge.net/](http://dfast.sourceforge.net/)

---

### Post by Kow on 2007-10-31
[http://women.debian.org/wiki/English/PackagingTutorial](http://women.debian.org/wiki/English/PackagingTutorial)
[http://women.debian.org/wiki/English/AdvancedBuildingTips](http://women.debian.org/wiki/English/AdvancedBuildingTips)
[http://women.debian.org/wiki/English/BuildingWithoutHelper](http://women.debian.org/wiki/English/BuildingWithoutHelper)

In reality, building an "ubuntu package" is building a debian package. In fact, there are quite a few ubuntu packages without the "ubuntu" name in them, meaning they are in fact straight from debian. I guess what I'm really saying is, the two are the same. In all likelihood there already exist a wxdownloader .deb somewhere that *should* work on ubuntu. If it does not work then apt-get remove it. :)

---

