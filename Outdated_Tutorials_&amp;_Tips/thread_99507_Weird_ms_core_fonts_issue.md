---
title: "Weird ms core fonts issue"
date: 2005-12-05
forum: Outdated Tutorials &amp; Tips
---

### Post by arpunk on 2005-12-05
It worked a few days ago, but then i went to another box and tried to install msttcorefonts and this happened:
```

$ sudo apt-get install msttcorefonts
Reading package lists... Done
Building dependency tree... Done
Package msttcorefonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package msttcorefonts has no installation candidate
$

```
And apt-cache shows me:
```

$ sudo apt-cache search msttcorefonts
openoffice.org2 - OpenOffice.org Office suite version 2.0
openoffice.org - high-quality office productivity suite
$ sudo apt-get install openoffice.org2
Reading package lists... Done
Building dependency tree... Done
openoffice.org2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
$

```
Anyone have any idea what happened? Yes, i have all the repositories up to date and enabled.

---

### Post by christooss on 2005-12-14
Do you have backports and all extra repositories in you sources.list?

---

