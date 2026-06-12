---
title: "installing gparted, broke ntfs write support -- traced to add-on nftsprogs"
date: 2011-10-20
forum: New to Ubuntu
---

### Post by Jmob on 2011-10-20
Just a note to folks--this started out as a help post, but I figured it out as I was writing it.  Installing the "ntfsprogs" addon with gparted removes a package called ntfs-3g.  In my case that broke write support for NTFS, ostensibly due to an ownership/permissions issue.

Anyway, I didn't attempt to run both packages, I simply replaced the older one, and support returned.  Gparted's a pretty popular package, but unless someone more skilled than I explains the utility of ntfsprogs, it can safely and should wisely be avoided.

---

### Post by gsmanners on 2011-10-20
This is a packaging issue in gparted (it suggests ntfsprogs which is provided by ntfs-3g).

---

