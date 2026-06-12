---
title: "sources.list error...."
date: 2006-03-23
forum: Repositories &amp; Backports
---

### Post by yarvin on 2006-03-23
whenever I run apt-get update I get this error

> Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages)


what should I do?

---

### Post by aysiu on 2006-03-23
Get rid of the duplicate.

Can you post the output of this command? ```
cat /etc/apt/sources.list
```

---

