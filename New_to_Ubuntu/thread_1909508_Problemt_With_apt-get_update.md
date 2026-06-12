---
title: "Problemt With apt-get update"
date: 2012-01-15
forum: New to Ubuntu
---

### Post by l337monk on 2012-01-15
Total noob, sorry if this is an obvious question.

Current system:
root@Monkery:~# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 9.10
Release:        9.10
Codename:       karmic

When i try to run apt-get update, this is my output, why am i getting 404's? is this because I'm running an older version of the system? Did my sources file get corrupted? How would i go about fixing this?

Thanks for your help, find the output below...


root@Monkery:~# apt-get update
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages
  404  Not Found [IP: 91.189.92.183 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
  404  Not Found [IP: 91.189.92.167 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Packages
  404  Not Found [IP: 91.189.92.183 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
  404  Not Found [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
  404  Not Found [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
  404  Not Found [IP: 91.189.92.167 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages
  404  Not Found [IP: 91.189.92.183 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources
  404  Not Found [IP: 91.189.92.183 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Sources
  404  Not Found [IP: 91.189.92.183 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Sources
  404  Not Found [IP: 91.189.92.183 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Packages
  404  Not Found [IP: 91.189.92.183 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
  404  Not Found [IP: 91.189.92.167 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
  404  Not Found [IP: 91.189.88.40 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
  404  Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Packages
  404  Not Found [IP: 91.189.92.183 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Packages
  404  Not Found [IP: 91.189.92.183 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Sources
  404  Not Found [IP: 91.189.92.183 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Sources
  404  Not Found [IP: 91.189.92.183 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Sources
  404  Not Found [IP: 91.189.92.183 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
  404  Not Found [IP: 91.189.92.167 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
  404  Not Found [IP: 91.189.88.40 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
  404  Not Found [IP: 91.189.88.40 80]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources.gz)  404  Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.183 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.183 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.183 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.gz)  404  Not Found [IP: 91.189.92.183 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.92.183 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz)  404  Not Found [IP: 91.189.92.183 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.183 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources.gz)  404  Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.183 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.183 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.gz)  404  Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.gz)  404  Not Found [IP: 91.189.92.183 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.92.183 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.gz)  404  Not Found [IP: 91.189.92.183 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz)  404  Not Found [IP: 91.189.88.40 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
root@Monkery:~#

---

### Post by oldos2er on 2012-01-15
Karmic is end-of-life, its repositories have moved to old-releases and are no longer being updated. You should upgrade to 10.04 or newer.

---

### Post by Michael Dooley on 2012-01-15
The 404's are because karmic is no longer supported. However, you can still update your karmic installation if you so choose.

Please see this thread for a solution to your immediate problem. It includes the old-release URLs for the karmic user. 

[http://ubuntuforums.org/showthread.php?t=1895629](http://ubuntuforums.org/showthread.php?t=1895629)

---

