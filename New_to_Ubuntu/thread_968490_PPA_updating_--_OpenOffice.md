---
title: "PPA updating -- OpenOffice"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by brandoncolorado on 2008-11-02
Hello,

I understand how to add PPA repositories to my sources.list file.  I wanted OpenOffice3, so I added these to my sources.list file:

```
## Openoffice.org
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```

Here are some very basic questions I have:

1)  If I now remove these repositories from my sources.list file, will the software continue to update?

2)  What happens when the official Ubuntu repositories begin to support OpenOffice3 (with Jaunty Jackalope)?  Is Ubuntu going to install OpenOffice twice, or will the PPA repository fail to update the installation?  Will I have to remove the PPA repository or OpenOffice to allow for true Ubuntu support again?


Thank you

---

### Post by igknighted on 2008-11-02
1) No, if you don't have the repositories activated in your sources.list, it won't look for updates there.

2) Apt will always grab the newest version of a package available, no matter which repository (official, PPA, etc.).

---

