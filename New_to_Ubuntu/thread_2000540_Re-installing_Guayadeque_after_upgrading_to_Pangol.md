---
title: "Re-installing Guayadeque after upgrading to Pangolin"
date: 2012-06-09
forum: New to Ubuntu
---

### Post by RayArdia on 2012-06-09
Since the upgrade, although I can apparently still open Guayadeque, the Software Centre tells me that it is not installed. When I try to install it I get this report:-
installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 213516 files and directories currently installed.)
Unpacking guayadeque (from .../guayadeque_0.3.5~ds0-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/guayadeque_0.3.5~ds0-1_i386.deb (--unpack):
 trying to overwrite '/usr/share/pixmaps/guayadeque.png', which is also in package guayadeque-svn 1803~oneiric-1
No apport report written because MaxReports is reached already
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/guayadeque_0.3.5~ds0-1_i386.deb
Error in function: 
I want to remove any other music players and use only Guayadeque, how do I go about this please?

---

### Post by anonbeat on 2012-06-10
> **RayArdia said:**
> Since the upgrade, although I can apparently still open Guayadeque, the Software Centre tells me that it is not installed. When I try to install it I get this report:-
installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 213516 files and directories currently installed.)
Unpacking guayadeque (from .../guayadeque_0.3.5~ds0-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/guayadeque_0.3.5~ds0-1_i386.deb (--unpack):
 trying to overwrite '/usr/share/pixmaps/guayadeque.png', which is also in package guayadeque-svn 1803~oneiric-1
No apport report written because MaxReports is reached already
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/guayadeque_0.3.5~ds0-1_i386.deb
Error in function: 
I want to remove any other music players and use only Guayadeque, how do I go about this please?

You are having this problem because you had installed guayadeque-svn and now you are trying to install from official repository. I recommend you to add the ppa:anonbeat/guayadeque and install guayadeque-svn which has more fixes than the actual version in repositories.
If you want the official repositories version remove guayadeque-svn and install guayadeque packages.

```
sudo apt-get remove guayadeque-svn
sudo apt-get install guayadeque
```

---

