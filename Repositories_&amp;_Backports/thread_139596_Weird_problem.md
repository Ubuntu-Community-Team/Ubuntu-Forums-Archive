---
title: "Weird problem"
date: 2006-03-04
forum: Repositories &amp; Backports
---

### Post by qalimas on 2006-03-04
I'm running Kubuntu 5.10, I don't know what's wrong, but no matter what package I try (in here it was ZSNES), I get this error.

> keith@klaptop:~$ sudo apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) breezy Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports Release
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) breezy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
Get:4 [http://kubuntu.org](http://kubuntu.org) breezy Release.gpg [189B]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) breezy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages
Hit [http://kubuntu.org](http://kubuntu.org) breezy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Sources
Err [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) breezy/main Packages
  404 Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Sources
Hit [http://kubuntu.org](http://kubuntu.org) breezy/main Packages
Get:6 [http://www.mirrorservice.org](http://www.mirrorservice.org) breezy Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://www.mirrorservice.org](http://www.mirrorservice.org) breezy Release
Hit [http://www.mirrorservice.org](http://www.mirrorservice.org) breezy/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [ftp://bolugftp.uni-bonn.de](ftp://bolugftp.uni-bonn.de) breezy Release.gpg
Get:7 [ftp://bolugftp.uni-bonn.de](ftp://bolugftp.uni-bonn.de) breezy Release [1793B]
Hit [ftp://bolugftp.uni-bonn.de](ftp://bolugftp.uni-bonn.de) breezy/main Packages
Fetched 1987B in 2s (799B/s)
Failed to fetch [http://mirror.cc.columbia.edu/pub/software/kde/stable/3.5.1/kubuntu/dists/breezy/main/binary-i386/Packages.gz](http://mirror.cc.columbia.edu/pub/software/kde/stable/3.5.1/kubuntu/dists/breezy/main/binary-i386/Packages.gz)  404 Not Found
Reading package lists... Done
W: Couldn't stat source package list [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) breezy/main Packages (/var/lib/apt/lists/mirror.cc.columbia.edu_pub_software_kde_stable_3.5.1_kubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
keith@klaptop:~$ sudo apt-get install zsnes
Reading package lists... Done
Building dependency tree... Done
Package zsnes is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) breezy/main Packages (/var/lib/apt/lists/mirror.cc.columbia.edu_pub_software_kde_stable_3.5.1_kubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package zsnes has no installation candidate

---

### Post by Ptero-4 on 2006-03-05
You got some dead repos in your sources.list. And odds are that the app you're trying to install is in one of the dead repos.

---

