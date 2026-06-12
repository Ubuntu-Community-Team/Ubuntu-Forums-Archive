---
title: "Need answer soon"
date: 2007-05-03
forum: Programming Talk
---

### Post by Gefox4 on 2007-05-03
When I choose Add/Remove, then I choose some packages and click OK, the packages will be download and install. But where will the packages be in??? :confused:

---

### Post by 5-HT on 2007-05-03
The .debs themselves will be downloaded to /var/cache/apt/archives/
As to the installed files, they will be installed into various places in the filesystem as stipulated by the package itself--usually with the bulk in /usr. To see where individual files of a package are placed you can use synaptic (look in the right-click properties tab for a package) or by using the 'whereis' command (refer to 'man whereis' from a terminal for futher information).

---

