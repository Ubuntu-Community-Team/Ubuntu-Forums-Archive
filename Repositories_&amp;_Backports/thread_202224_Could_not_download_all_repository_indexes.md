---
title: "Could not download all repository indexes"
date: 2006-06-23
forum: Repositories &amp; Backports
---

### Post by grw on 2006-06-23
Can anyone help me with this?

I have just installed Dapper and was then trying to use add/remove applications. It tells me my repositories are out of date. When I reload them I get this message:

'Could not download all repository indexes. The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.'

I'll paste sudo apt-get update and sources.list info below. I am behind a proxy server and on a network with a 255.255.255.255 netmask (which is valid) in case this is relevant. I had to alter my dhclient-script to allow me to access the network (see [http://www.ubuntuforums.org/showthread.php?t=200297](http://www.ubuntuforums.org/showthread.php?t=200297) ), but now firefox works. Apt-get doesn't though.

Any ideas?

sudo apt-get update: 

Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Errhttp://security.ubuntu.com dapper-security/main Packages
  302 Found
Errhttp://security.ubuntu.com dapper-security/restricted Packages
  302 Found
Errhttp://security.ubuntu.com dapper-security/main Sources
  302 Found
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Packages
Errhttp://security.ubuntu.com dapper-security/restricted Sources
  302 Found
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Sources
Errhttp://gb.archive.ubuntu.com dapper/main Packages
  302 Found [IP: 85.133.25.7 80]
Errhttp://gb.archive.ubuntu.com dapper/restricted Packages
  302 Found [IP: 85.133.25.7 80]
Errhttp://gb.archive.ubuntu.com dapper/main Sources
  302 Found [IP: 85.133.25.7 80]
Errhttp://gb.archive.ubuntu.com dapper/restricted Sources
  302 Found [IP: 85.133.25.7 80]
Errhttp://gb.archive.ubuntu.com dapper-updates/main Packages
  302 Found [IP: 85.133.25.7 80]
Errhttp://gb.archive.ubuntu.com dapper-updates/restricted Packages
  302 Found [IP: 85.133.25.7 80]
Errhttp://gb.archive.ubuntu.com dapper-updates/main Sources
  302 Found [IP: 85.133.25.7 80]
Errhttp://gb.archive.ubuntu.com dapper-updates/restricted Sources
  302 Found [IP: 85.133.25.7 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz)  302 Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz)  302 Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz)  302 Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz)  302 Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz)  302 Found [IP: 85.133.25.7 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz)  302 Found [IP: 85.133.25.7 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz)  302 Found [IP: 85.133.25.7 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz)  302 Found [IP: 85.133.25.7 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz)  302 Found [IP: 85.133.25.7 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz)  302 Found [IP: 85.133.25.7 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz)  302 Found [IP: 85.133.25.7 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz)  302 Found [IP: 85.133.25.7 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

sources.list

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by CameronCalver on 2006-06-23
try this source list and see if it works



deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
#created by arniedappersecond

---

### Post by grw on 2006-06-23
I tried, but I have the same problem.

---

