---
title: "digikam in 8.10 has too many dependencies."
date: 2008-11-16
forum: Packaging and Compiling Programs
---

### Post by mmcmonster on 2008-11-16
I opened [Bug 298784]("https://bugs.launchpad.net/ubuntu/+source/digikam/+bug/298784") for this:

On a fresh installation of Ubuntu (not kubuntu) 8.10, doing a "apt-get install digikam" will install both qt3 and qt4, dolphin and konqueror, k3b, kmail, and just about everything else in kubuntu, it seems.

I suggest that this be cut down a bit.  Maybe digikam is installing a meta package that is pulling in everything in kubuntu?

Note that digikam installed in Ubuntu 8.10 appears to be using the KDE3 graphics (qt3), so none of the qt4 stuff should be installed, right?

---

### Post by Foxmike on 2009-05-14
Maybe it has been solved already, but let's answer it anyway.

Apt is configured to do (by default) install the following:
* Direct dependencies
* Recommended dependencies

Those "recommends" are not absolutely required in order to operate the software, but they add much to it and usually people want them installed as well, so the Ubuntu developpers did make that the default behavior of the package manager.

In digikam's recommends there is dolphin, konqueror and k3b (which uses qt3, hence the qt3 dependency). 

I think that the following command will help you:

```
sudo apt-get install --no-install-recommends digikam
```

Hope it helps!

---

