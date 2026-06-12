---
title: "The package system is broken?"
date: 2012-09-22
forum: New to Ubuntu
---

### Post by Hadley C on 2012-09-22
Hello,
I'm not an absolute beginner when it comes to linux. I was recently trying to do a software update when I got an error saying that "The package system is broken".

Here is a screenshot. It does a better job of explaining the problem than I could.
[http://i679.photobucket.com/albums/vv160/Hadleyiztwisted/Screenshotfrom2012-09-22113430_zps292cf198.png](http://i679.photobucket.com/albums/vv160/Hadleyiztwisted/Screenshotfrom2012-09-22113430_zps292cf198.png)

Thank you,

Hadley

---

### Post by jrog on 2012-09-22
> **Hadley C said:**
> Hello,
I'm not an absolute beginner when it comes to linux. I was recently trying to do a software update when I got an error saying that "The package system is broken".

Here is a screenshot. It does a better job of explaining the problem than I could.
[http://i679.photobucket.com/albums/vv160/Hadleyiztwisted/Screenshotfrom2012-09-22113430_zps292cf198.png](http://i679.photobucket.com/albums/vv160/Hadleyiztwisted/Screenshotfrom2012-09-22113430_zps292cf198.png)

Thank you,

Hadley
A couple questions. Where did you try to install ia32-libs-multiarch:i386 from (if you did; I can't tell from the pictures what exactly you have been trying to do)? Have you been installing software manually (i.e., not using apt-get, perhaps using dpkg)? Finally, what happens if you type this at the command line:

```
sudo dpkg --configure -a
sudo apt-get install -f
```?

---

### Post by Hadley C on 2012-09-22
Thank you for your response!

Here is what returns when I run those commands:

```

hadley@hadley-U36SD:~$ sudo dpkg --configure -a
[sudo] password for hadley: 
dpkg: dependency problems prevent configuration of ia32-libs-multiarch:
 ia32-libs-multiarch depends on libsane; however:
  Package libsane:i386 is not installed.

dpkg: error processing ia32-libs-multiarch (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ia32-libs:
 ia32-libs depends on ia32-libs-multiarch; however:
  Package ia32-libs-multiarch is not configured yet.

dpkg: error processing ia32-libs (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ia32-libs-multiarch
 ia32-libs
hadley@hadley-U36SD:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libsane:i386
Suggested packages:
  hpoj:i386 hplip:i386 libsane-extras:i386 sane-utils:i386
The following NEW packages will be installed:
  libsane:i386
0 upgraded, 1 newly installed, 0 to remove and 18 not upgraded.
2 not fully installed or removed.
Need to get 0 B/3,734 kB of archives.
After this operation, 8,970 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 240932 files and directories currently installed.)
Unpacking libsane:i386 (from .../libsane_1.0.23-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libsane_1.0.23-0ubuntu1_i386.deb (--unpack):
 trying to overwrite shared '/etc/sane.d/kodakaio.conf', which is different from other instances of package libsane:i386
Errors were encountered while processing:
 /var/cache/apt/archives/libsane_1.0.23-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
hadley@hadley-U36SD:~$

```

I actually have no idea where I installed the package from. Like I said, I'm a complete newbie.

Also when I open the software center, it wants to try to repair the package catalog. It fails to do so and returns this message:

```
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
(Reading database ... 240932 files and directories currently installed.)
Unpacking libsane:i386 (from .../libsane_1.0.23-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libsane_1.0.23-0ubuntu1_i386.deb (--unpack):
 trying to overwrite shared '/etc/sane.d/kodakaio.conf', which is different from other instances of package libsane:i386
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 /var/cache/apt/archives/libsane_1.0.23-0ubuntu1_i386.deb
Error in function: 
dpkg: dependency problems prevent configuration of ia32-libs-multiarch:
 ia32-libs-multiarch depends on libsane; however:
  Package libsane:i386 is not installed.

dpkg: error processing ia32-libs-multiarch (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ia32-libs:
 ia32-libs depends on ia32-libs-multiarch; however:
  Package ia32-libs-multiarch is not configured yet.

dpkg: error processing ia32-libs (--configure):
 dependency problems - leaving unconfigured

```

---

### Post by Frogs Hair on 2012-09-22
You can try the following .```
sudo apt-get clean
``` ```
sudo apt-get update
``````
sudo apt-get upgrade
```

---

### Post by dasyentist on 2013-02-20
> **Frogs Hair said:**
> You can try the following .```
sudo apt-get clean
``` ```
sudo apt-get update
``````
sudo apt-get upgrade
```

thank you ! 


ran those 3 command then it told me to run "apt-get -f install"  and it fixed the problem !  thank you !

---

