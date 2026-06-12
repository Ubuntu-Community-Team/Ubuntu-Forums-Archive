---
title: "Cant upgrade from 12.04"
date: 2013-06-16
forum: New to Ubuntu
---

### Post by ro12 on 2013-06-16
Hi there,I can't install any programmes or do an upgrade.
When I try to upgrade in terminal I get this message:
debconf: apt-extracttemplates failed: No such file or directory
Extracting templates from packages: 70%E: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: No such file or directory
Extracting templates from packages: 88%E: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: No such file or directory
Extracting templates from packages: 100%
dpkg: error: failed to open package info file `/var/lib/dpkg/available' for reading: No such file or directory
Error in function:




A fatal error occurred


Please report this as a bug and include the files
/var/log/dist-upgrade/main.log and /var/log/dist-upgrade/apt.log in
your report. The upgrade has aborted.
Your original sources.list was saved in
/etc/apt/sources.list.distUpgrade.


SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2)






Could not install the upgrades


The upgrade has aborted. Your system could be in an unusable state. A
recovery will run now (dpkg --configure -a).


dpkg: error: duplicate file trigger interest for filename `/usr/lib/gdk-pixbuf-2.0/2.10.0/loaders' and package `libgdk-pixbuf2.0-0'
dpkg-query: error: duplicate file trigger interest for filename `/usr/lib/gdk-pixbuf-2.0/2.10.0/loaders' and package `libgdk-pixbuf2.0-0'


Upgrade complete


The upgrade has completed but there were errors during the upgrade
process.


Any ideas much appreciated.

---

### Post by Sef on 2013-06-16
what happens when you run this code first:

```
sudo apt-get update
```.

If it runs well, then rerun ```
sudo apt-get upgrade
```.

---

