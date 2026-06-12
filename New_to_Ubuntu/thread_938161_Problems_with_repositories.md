---
title: "Problems with repositories"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by fredscripts on 2008-10-04
When I try to download some software through aptget, for example eclipse

```
sudo apt-get install eclipse
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Recommended packages:
  eclipse-gcj
The following NEW packages will be installed:
  eclipse
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 129kB of archives.
After this operation, 426kB of additional disk space will be used.
Err http://es.archive.ubuntu.com hardy/universe eclipse 3.2.2-5ubuntu2
  403 Forbidden
Failed to fetch http://es.archive.ubuntu.com/ubuntu/pool/universe/e/eclipse/eclipse_3.2.2-5ubuntu2_i386.deb  403 Forbidden
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

So it seems there are problems with spanish repositories, should I add any lines to source.list? my internet connection is working fine.

Thank you very much!!

---

### Post by Paqman on 2008-10-04
Go to System > Admin > Software Sources, click on the "download from" and "select best server".

It'll automatically locate a server that you have a good connection to.

---

### Post by fredscripts on 2008-10-04
Thanks!!!

---

