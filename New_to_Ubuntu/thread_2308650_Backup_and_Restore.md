---
title: "Backup and Restore"
date: 2016-01-04
forum: New to Ubuntu
---

### Post by Ed10 on 2016-01-04
I have a ton of Linux downloaded programs. If I backup the archived download files will they be "easy" to reinstall when I install Ubuntu on a new machine?

---

### Post by ajgreeny on 2016-01-05
Downloaded from where, and will the reinstallation of Ubuntu be the same version as the current?

If the programs are in the form of .deb archive packages from the repos of Ubuntu and the new version is the same as the old, it should be possible to reinstall them either by copying the .debs to /var/cache/apt/archives folder and then using the normal installation methods, or possibly using gdebi.

If the programs are from an outside source it is impossible to say what you might be able to do as it will depend on many things that you have told us nothing about.

---

