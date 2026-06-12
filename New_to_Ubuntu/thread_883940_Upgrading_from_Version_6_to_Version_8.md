---
title: "Upgrading from Version 6 to Version 8"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by chemjeff on 2008-08-08
Hello,
I am trying to upgrade from Version 6 to Version 8.  However I get the following errors:

W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.bz2)  Hash Sum mismatch
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.bz2)  Hash Sum mismatch
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.bz2)  Hash Sum mismatch
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.bz2)  Hash Sum mismatch
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.bz2)  Hash Sum mismatch
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.bz2)  Hash Sum mismatch
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.bz2)  Hash Sum mismatch
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.bz2)  Hash Sum mismatch
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.bz2)  Hash Sum mismatch
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/source/Sources.bz2)  Hash Sum mismatch
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.bz2)  Hash Sum mismatch
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.bz2)  Hash Sum mismatch
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.bz2)  Hash Sum mismatch
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.bz2)  Hash Sum mismatch
, E:Some index files failed to download, they have been ignored, or old ones used instead.

Is this a problem with my installation procedure or with something else? Any assistance you could provide would be helpful.

Thanks,
-Jeff

---

### Post by quantumstitch on 2008-08-08
I think you have to do this stepwise. 6->7->8.

---

### Post by philinux on 2008-08-08
[http://ward.vandewege.net/blog/2008/07/upgrading-from-dapper-to-hardy-hash-sum-mismatch/](http://ward.vandewege.net/blog/2008/07/upgrading-from-dapper-to-hardy-hash-sum-mismatch/)

sudo aptitude upgrade
sudo aptitude dist-upgrade
sudo aptitude install update-manager-core
sudo do-release-upgrade

---

