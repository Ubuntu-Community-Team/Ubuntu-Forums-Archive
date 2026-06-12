---
title: "Cannot upgrade to 7.10 to 8.04"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by fredscripts on 2008-10-04
Hi!!

When trying to upgrade through the update manager to 8.04...

At second step "Setting new software channels..."

CRASH!:

Error during update

A problem occurred during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://es.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz](http://es.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz) 403 Forbidden
Failed to fetch [http://es.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz](http://es.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz) 403 Forbidden
Failed to fetch [http://es.archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.gz](http://es.archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.gz) 403 Forbidden
Failed to fetch [http://es.archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.gz](http://es.archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.gz) 403 Forbidden
Failed to fetch [http://es.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.gz](http://es.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.gz) 403 Forbidden
Failed to fetch [http://es.archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.gz](http://es.archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.gz) 403 Forbidden
Failed to fetch [http://es.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.gz](http://es.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.gz) 403 Forbidden
Failed to fetch [http://es.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz](http://es.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz) 403 Forbidden
Failed to fetch [http://es.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz](http://es.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz) 403 Forbidden
Failed to fetch [http://es.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz](http://es.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz) 403 Forbidden
Failed to fetch [http://es.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.gz](http://es.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.gz) 403 Forbidden
Failed to fetch [http://es.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.gz](http://es.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.gz) 403 Forbidden
Failed to fetch [http://es.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz](http://es.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz) 403 Forbidden
Failed to fetch [http://es.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.gz](http://es.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.gz) 403 Forbidden
Failed to fetch [http://es.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz](http://es.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz) 403 Forbidden
Failed to fetch [http://es.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz](http://es.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz) 403 Forbidden


Is there any way I can solve this issue? Or I should start downloading/ordering the 8.04 CD...?


Thank you very much!!

---

### Post by tuxxy on 2008-10-04
You have read the [update guide?]("https://help.ubuntu.com/community/HardyUpgrades")

---

### Post by fredscripts on 2008-10-04
Yeah sure, the crash happens after I pressed the upgrade button on the update manager...

---

### Post by sdowney717 on 2008-10-04
Forbidden

You don't have permission to access /ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz on this server.

Additionally, a 403 Forbidden error was encountered while trying to use an ErrorDocument to handle the request.
Apache Server at es.archive.ubuntu.com Port 80

yeah, i get that as well when clicking on your link. Seems to me the source list for the upgrade files is pointing to the wrong place

---

