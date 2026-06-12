---
title: "software installer"
date: 2011-12-11
forum: New to Ubuntu
---

### Post by scorpion103068 on 2011-12-11
trying to install gparted i get package operation failed then i click ok then i getitems cannot be installed or removed until the package catalog is repaired so i choose repair it then asks for my password then loops and starts all over again....HELP

---

### Post by gennatolls on 2011-12-11
Open up a terminal and try the following:
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
```
sudo apt-get install gparted
```

Good luck.

---

