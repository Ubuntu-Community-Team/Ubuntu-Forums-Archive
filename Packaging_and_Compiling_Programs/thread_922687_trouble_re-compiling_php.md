---
title: "trouble re-compiling php"
date: 2008-09-17
forum: Packaging and Compiling Programs
---

### Post by isho on 2008-09-17
I'm trying to re-compile php with ming support. I already have php running with apache2

It fails when I run **apt-get source** But it seems like it can't find one of the package servers. Any idea what I should do next?


$ apt-get source php5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Need to get 9471kB of source archives.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main php5 5.2.3-1ubuntu6.3 (dsc)
  404 Not Found [IP: 91.189.88.46 80]
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main php5 5.2.3-1ubuntu6.3 (tar) [9342kB]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main php5 5.2.3-1ubuntu6.3 (diff)                                                 
  404 Not Found [IP: 91.189.88.46 80]
Fetched 9342kB in 1m3s (147kB/s)                                                                                                 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/php5/php5_5.2.3-1ubuntu6.3.dsc](http://us.archive.ubuntu.com/ubuntu/pool/main/p/php5/php5_5.2.3-1ubuntu6.3.dsc)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/php5/php5_5.2.3-1ubuntu6.3.diff.gz](http://us.archive.ubuntu.com/ubuntu/pool/main/p/php5/php5_5.2.3-1ubuntu6.3.diff.gz)  404 Not Found [IP: 91.189.88.46 80]
E: Failed to fetch some archives.

---

### Post by InfinityCircuit on 2008-09-17
apt-get update and try again.  You were probably caught at a bad mirror sync.

---

