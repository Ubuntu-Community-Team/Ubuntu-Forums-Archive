---
title: "I need to upgrade a 10.10 installation to the current version of Ubuntu"
date: 2013-09-10
forum: New to Ubuntu
---

### Post by ccF8R8e on 2013-09-10
I cannot believe I did not find an answer to this when I searched the forums. I inherited an old server at my new job.  As the Sr. Web Developer I am now the Server admin.  Here is the print out to my current version:

Distributor ID: Ubuntu
Description:    Ubuntu 10.10
Release:        10.10
Codename:       maverick

Every time I try to upgrade or dist-upgrade in apt-get I receive a stream of  404  Not Found.  I searched ask Ubuntu and got the latest sources.list but that did not solve my problem.

What is the correct process?


Thanks.

Scott

---

### Post by oldos2er on 2013-09-10
10.10 reached its end of life in April 2012, [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
If possible you should do a clean install of 12.04 server edition, which will be supported for five years.

---

### Post by deadflowr on 2013-09-10
Definite +1 on doing a fresh/clean install of 12.04 or newer.
Backup what you need.
I'd say do a fresh install because then you can at least have full knowledge of everything that's on it, where as inheriting an already setup one, you might not.

---

### Post by Jonathan Precise on 2013-09-10
> **ccF8R8e said:**
> I cannot believe I did not find an answer to this when I searched the forums. I inherited an old server at my new job.  As the Sr. Web Developer I am now the Server admin.  Here is the print out to my current version:

Distributor ID: Ubuntu
Description:    Ubuntu 10.10
Release:        10.10
Codename:       maverick

Every time I try to upgrade or dist-upgrade in apt-get I receive a stream of  404  Not Found.  I searched ask Ubuntu and got the latest sources.list but that did not solve my problem.

What is the correct process?


Thanks.

Scott

Change archive.ubuntu.com to old-releases.ubuntu.com. Then:

```
sudo do-release-upgrade
```

to upgrade to ubuntu 11.04.
Do the change of the sources.list again. Repeat until you arive at 12.04 LTS.

Or just do a clean install (no formatting)

---

