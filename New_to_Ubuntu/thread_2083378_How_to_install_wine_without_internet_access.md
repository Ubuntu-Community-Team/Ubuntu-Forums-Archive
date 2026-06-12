---
title: "How to install wine without internet access?"
date: 2012-11-12
forum: New to Ubuntu
---

### Post by vickykx68 on 2012-11-12
> **jre6 said:**
> Installing all of the dependencies is not needed. You can just download these to install wine:
cabextract : [http://packages.ubuntu.com/natty/cabextract](http://packages.ubuntu.com/natty/cabextract)
gettext : [http://packages.ubuntu.com/natty/gettext](http://packages.ubuntu.com/natty/gettext)
libmpg123-0 : [http://packages.ubuntu.com/natty/libmpg123-0](http://packages.ubuntu.com/natty/libmpg123-0)
libopenal1 : [http://packages.ubuntu.com/natty/libopenal1](http://packages.ubuntu.com/natty/libopenal1)
wine1.3 : [http://packages.ubuntu.com/natty/wine1.3]("http://packages.ubuntu.com/natty/wine")

Transfer these packages to your home folder, and type in a terminal:
```

cd ~
sudo dpkg -i cabextract*.deb gettext*.deb libmpg123-0*.deb libopenal1*.deb wine1.3*.deb

```And wine will be installed

All links specified are broken...pls update

---

### Post by oldos2er on 2012-11-12
Post moved to its own thread.

Did you try replacing "natty" with whichever release you're running?

---

