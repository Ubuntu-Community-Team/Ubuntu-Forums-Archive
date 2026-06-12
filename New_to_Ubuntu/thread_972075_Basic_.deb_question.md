---
title: "Basic .deb question"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by brandoncolorado on 2008-11-05
If I install something with a .deb file, will that software be automatically updated like everything I install with a package manager like synaptic?

---

### Post by LowSky on 2008-11-05
Most times yes, DEBs are based on Debian, and because there are some differences to the system with Ubuntu, some things will not work all the time.

---

### Post by drs305 on 2008-11-05
Synaptic can only update packages which are in the repositories it checks for updates. So if the package maintainer is not listed in the ubuntu or third-party respositories, including those you have added, it won't know of updates and thus can't update it. 

An example of one that *would* be updated would be googleearth. If you add the medibuntu repository, that repository will be checked for updates. 

An example of one that would not would be a deb you created with checkinstall and then installed yourself. If the deb package didn't exist in a repository named in the sources.list it won't be updated.

On the other hand, having a package listed in synaptic has the advantage of having an easy way to uninstall it should that become necessary or desired even if it can't be updated.

---

### Post by REDace0 on 2008-11-05
If you use dpkg -i PACKAGE_NAME.deb, it will install it just like apt-get and aptitude do, adding it to your list of installed packages, but unless you have a repository for it in System>Administration>Software Sources or in /etc/apt/sources.list, you won't see new versions unless you venture out on to the web and find the new .deb yourself.

---

