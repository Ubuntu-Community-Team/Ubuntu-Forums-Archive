---
title: "Can't install dev packages in general"
date: 2015-01-04
forum: Packaging and Compiling Programs
---

### Post by katz2 on 2015-01-04
Hi!

I am trying to set up my first linux development environment on a 64bit Xubuntu 14.04. The problem is I can't install numerous dev and build related packages, because some of my dependencies are "too new".

For example, I am trying to install now xorg-dev and libglu1-mesa-dev. Both of these are failing with:
```
Depends: <some package> but it is not going to be installed
```
Walking down on the dependency tree the cause is always having a mismatching version for a package. Example:
```
libfontconfig1-dev : Depends: libfontconfig1 (= 2.11.0-0ubuntu4) but 2.11.0-0ubuntu4.1 is to be installed
```
```
libgl1-mesa-dev : Depends: libgl1-mesa-glx (= 10.1.0-4ubuntu5) but 10.1.3-0ubuntu0.2 is to be installed
```

In some cases I was able to fix these issues by downgrading my package versions using apt-get install <package>=<older version>.
Unfortunately sometimes this doesn't work, I simply get:```

The following extra packages will be installed:
  libfontconfig1
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

I've tried most broken package fixing tipps I came across, but most of the issues were not related. I am not sure whether this is related to xubuntu itself or I just made a newbie mistake along the way. Any help is greatly appriciated.

---

### Post by mc4man on 2015-01-04
Please open Software & Updates > click on the Updates tab & make sure that first 2 repos are enabled (trusty-security, trusty-updates
If one or both aren't then enable > reload your sources & you should be able to get the newer packages.

If they are enabled & newer versions aren't avail. then switch your Source in Software & Updates > Download from.

If still with issue post - 
```
apt-cache policy libfontconfig*
```
```
 apt-cache policy libgl1-mesa-dev
```

---

### Post by katz2 on 2015-01-05
I did indeed have trusty-security and trusty-updates disabled, enabling them solved the issue. Thanks!

---

