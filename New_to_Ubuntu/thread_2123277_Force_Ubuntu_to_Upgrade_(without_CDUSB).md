---
title: "Force Ubuntu to Upgrade (without CD/USB)"
date: 2013-03-07
forum: New to Ubuntu
---

### Post by mcclunyboy on 2013-03-07
Hi,

Ubuntu version = pretty old....Got a new PC which I am hoping to use, it doesn't have USB/CD and when I issue the following commands it fails to update:

```
uname -a
Linux NP 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux
```

```
cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"

```

```
sudo apt-get update
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources.gz  404  Not Found [IP: 91.189.91.13 80]
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz  404  Not Found [IP: 91.189.91.13 80]
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/source/Sources.gz  404  Not Found [IP: 91.189.91.13 80]

```

```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

I have also tried running the apt-get commands as root without success. 

Is there anyway I can force it to look in the right place for upgrades, where ever that is?

Edit - what are the correct repositories for downloading updates (and where do I add them in this version of Ubuntu?)?

---

### Post by mcclunyboy on 2013-03-07
Quick Reply - found the answer I was looking for in the Ubuntu Community...Apologies for posting this a bit prematurely:

[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

---

### Post by Cheesemill on 2013-03-07
9.10 reached end of life in April 2011 and as such hasn't received any bug fixes or security updates for the last 2 years.
This also means that the repositories have been taken off-line.

You can install software and update your system to the point where it reached end-of-life by pointing your sources.list to the archived repositories at [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) but I would highly recommended a clean installation of a version of Ubuntu that is still being supported.

---

