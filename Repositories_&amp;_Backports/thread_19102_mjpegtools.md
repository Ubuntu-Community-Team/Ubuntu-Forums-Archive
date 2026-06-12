---
title: "mjpegtools"
date: 2005-03-10
forum: Repositories &amp; Backports
---

### Post by djp on 2005-03-10
I am currently running a warty installation but having trouble installing mjpegtools. My sources.list file looks like this:-

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) warty-backports main universe

However when I apt-get install mjpegtools, I receive the following information:-

Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mjpegtools: Depends: libmjpegtools0 (>= 1:1.6.2-0.6) but it is not going to be installed
              Depends: libpng12-0 (>= 1.2.8rel) but 1.2.5.0-7ubuntu1 is to be installed
              Depends: libquicktime1 (>= 0.9.3) but it is not going to be installed
              Depends: libsdl1.2debian (> 1.2.7+1.2.8) but 1.2.7-7 is to be installed
E: Broken packages

Any help would be most appreciated.

djp

---

