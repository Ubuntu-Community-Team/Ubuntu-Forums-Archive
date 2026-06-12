---
title: "problem with update-manager"
date: 2011-10-22
forum: New to Ubuntu
---

### Post by jaganpks on 2011-10-22
Hi,

while I tried to update my Ubuntu using update manager, it's giving an error

the error is 

E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.

Please help me in resolving this.

---

### Post by raja.genupula on 2011-10-22
Hi do this

do this 

```
sudo rm -vf /var/lib/apt/lists/*
sudo apt-get update
```

All the best.

---

### Post by jaganpks on 2011-10-24
Thanx Raja, it worked :)

---

