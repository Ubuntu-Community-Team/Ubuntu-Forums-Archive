---
title: "apt-get keeps updating the same package over and over"
date: 2016-05-29
forum: Packaging and Compiling Programs
---

### Post by actionmystique on 2016-05-29
Hello everyone,

I have created an [**experimental PPA**]("https://gitlab.com/jean-christophe-manciot/ppa") which hosts a lot of different packages for **Ubuntu 16.04**. The builds are as recent and stable as possible.
Everything works fine, except for 2 packages and I can't see what is different with the other ~ 400 ones.

With these "ntopng" and "libgegl-0.3-0", even though the local and remote packages are exactly the same, apt-get continues to offer an upgrade:
```
apt-cache policy libgegl-0.3-0
libgegl-0.3-0:
  Installed: 0.3.6-14
  Candidate: 0.3.6-14
  Version table:
     0.3.6-14 500
        500 https://gitlab.com/jean-christophe-manciot/ppa/raw/master/Ubuntu xenial/stable amd64 Packages
 *** 0.3.6-14 100
        100 /var/lib/dpkg/status
     0.3.4-1ubuntu2 500
        500 http://bouyguestelecom.ubuntu.lafibre.info/ubuntu xenial/universe amd64 Packages
```
```
apt-cache policy ntopng
ntopng:
  Installed: 2.2.1~git201605204.7b210f52-14
  Candidate: 2.2.1~git201605204.7b210f52-14
  Version table:
     2.2.1~git201605204.7b210f52-14 500
        500 https://gitlab.com/jean-christophe-manciot/ppa/raw/master/Ubuntu xenial/stable amd64 Packages
 *** 2.2.1~git201605204.7b210f52-14 100
        100 /var/lib/dpkg/status
     2.2.1~git20160512.689e38d9-14 500
        500 https://gitlab.com/jean-christophe-manciot/ppa/raw/master/Ubuntu xenial/stable amd64 Packages
     2.2+dfsg1-1build1 500
        500 http://bouyguestelecom.ubuntu.lafibre.info/ubuntu xenial/universe amd64 Packages
     2.2-14 500
        500 https://gitlab.com/jean-christophe-manciot/ppa/raw/master/Ubuntu xenial/stable amd64 Packages
```
For another package which doesn't experience any issue:
```
apt-cache policy git
git:
  Installed: 1:2.8.3-14
  Candidate: 1:2.8.3-14
  Version table:
 *** 1:2.8.3-14 500
        500 https://gitlab.com/jean-christophe-manciot/ppa/raw/master/Ubuntu xenial/stable amd64 Packages
        100 /var/lib/dpkg/status
     1:2.8.2-14 500
        500 https://gitlab.com/jean-christophe-manciot/ppa/raw/master/Ubuntu xenial/stable amd64 Packages
     1:2.7.4-0ubuntu1 500
        500 http://bouyguestelecom.ubuntu.lafibre.info/ubuntu xenial/main amd64 Packages
```
I can see a slight difference in the way the results are presented, but I'm unable to draw anything from it:
```
apt-get upgrade libgegl-0.3-0 ntopng git
Reading package lists... Done
Building dependency tree       
Reading state information... Done
git is already the newest version (1:2.8.3-14).
Calculating upgrade... Done
The following packages will be upgraded:
  libgegl-0.3-0 ntopng
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 69.4 MB of archives.
After this operation, 0 B of additional disk space will be used.
```
Anyone would care to share some tip?

---

