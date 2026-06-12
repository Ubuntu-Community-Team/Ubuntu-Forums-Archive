---
title: "Any I try to install anything I get this problem"
date: 2020-04-20
forum: New to Ubuntu
---

### Post by rajtad02 on 2020-04-20
sudo apt-get install --reinstall python-minimal python-lockfile
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 ibus-chewing : Depends: ibus (>= 1.5) but it is not going to be installed
 ibus-hangul : Depends: ibus (>= 1.3.99) but it is not going to be installed
 ibus-libpinyin : Depends: ibus but it is not going to be installed
 ibus-m17n : Depends: ibus but it is not going to be installed
 ibus-table : Depends: ibus (>= 1.5.0) but it is not going to be installed
 ibus-unikey : Depends: ibus (>= 1.3.99) but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

---

### Post by rajtad02 on 2020-04-20
I also get this problem a lot to 
dpkg: error processing package ibus (--remove):
 unable to securely remove '/usr/share/doc/ibus/changelog.Debian.gz.dpkg-tmp': Bad message
Errors were encountered while processing:
 ibus-libpinyin
 ibus
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Frogs Hair on 2020-04-20
> E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).         

Try the following
```
sudo apt -f install 
```

---

