---
title: "Can't install latest evolution updates"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by 71CH on 2008-07-17
Hi all
I can't install the latest evolution updates.  Can somebody help?

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  evolution evolution-common evolution-plugins
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 15.8MB/18.7MB of archives.
After this operation, 8192B disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main evolution-common 2.22.3.1-0ubuntu1 [15.8MB]
Fetched 15.8MB in 23s (662kB/s)                                                
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-common_2.22.3.1-0ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-common_2.22.3.1-0ubuntu1_all.deb)  Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


---

### Post by RomeReactor on 2008-07-17
Hi. Try what update manager recommends: open a terminal (Applications->Accessories->Terminal) and paste:
```
sudo apt-get update
```
and if that doesn't help:
```
sudo apt-get update --fix-missing
```

---

