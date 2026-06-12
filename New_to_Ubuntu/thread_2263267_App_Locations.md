---
title: "App Locations?"
date: 2015-01-30
forum: New to Ubuntu
---

### Post by rbengr on 2015-01-30
Hi,

Tonight I downloaded LibreOffice 4.4 through a ppa.  The apps show in the Installed Software area.  As you know, an app can't be launched from there.  I can't find the apps or their files using file Search.  Where are they sitting in the computer's file structure?  When you download an app is there a default save location?

Thanks

---

### Post by hamed.obaidy on 2015-01-31
in /usr/local

---

### Post by Holger_Gehrke on 2015-01-31
> **rbengr said:**
> When you download an app is there a default save location?



You got it from a ppa, so it's a .deb package that got installed through the package manager. What files where installed where you can find out by looking in the history in the software centre to find the names of the packages and then run
```

dpkg -L "package name"

```
(replace "package name" with the name of the each package from the installation history.

@hamed.obaidy
> 
in /usr/local


That would be for programs locally compiled from source and installed through "configure;make;sudo make install", which isn't the case here.

---

