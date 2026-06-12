---
title: "What version of KDE do I have?"
date: 2010-10-01
forum: Packaging and Compiling Programs
---

### Post by Colin@oxford on 2010-10-01
This seemingly daft question is caused by a problem with CMake.  I get this error when I try running CMake:
```

CMake Error at /usr/share/cmake-2.8/Modules/FindKDE4.cmake:98 (MESSAGE):
  ERROR: cmake/modules/FindKDE4Internal.cmake not found in
  /home/colin/.kde/share/apps;/usr/share/kde4/apps
```

So I wondered whether I actually have KDE4.  The repository is:

```

kdelibs4-dev
development files for the KDE core libraries
```

Which includes the file /usr/include/kde/version.h, but that claims that the version is 3.5.10.  So is this KDE4 or KDE3?

If it is KDE4, how do I fix the CMake problem?
If is it KDE3, how do I get KDE4?

---

### Post by SevenMachines on 2010-10-01
Its not a daft question, the naming scheme unfortunately is a bit confusing for some reason :) 

> $ apt-file search FindKDE4Internal.cmake 
kdelibs5-dev: /usr/share/kde4/apps/cmake/modules/FindKDE4Internal.cmakeso try,
> $ apt-get install kdelibs5-dev[EDIT] Just to add, this has caught me out any number of occasions, kdelibs5 for kde4, dont ask me why!

---

### Post by Colin@oxford on 2010-10-02
Thanks.  How very confusing!

---

