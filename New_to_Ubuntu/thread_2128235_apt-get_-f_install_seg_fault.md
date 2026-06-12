---
title: "apt-get -f install seg fault"
date: 2013-03-22
forum: New to Ubuntu
---

### Post by handimanmark on 2013-03-22
Hi I'm having a similar issue with aptitude. apt-get -f install won't complete with the following code returned:

```
mark@R2D2:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  python-aptdaemon python-aptdaemon.gtk3widgets python-aptdaemon.pkcompat
The following packages will be upgraded:
  python-aptdaemon python-aptdaemon.gtk3widgets python-aptdaemon.pkcompat
3 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
73 not fully installed or removed.
Need to get 0 B/126 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 315544 files and directories currently installed.)
Preparing to replace python-aptdaemon.pkcompat 0.43+bzr805-0ubuntu7 (using .../python-aptdaemon.pkcompat_0.43+bzr805-0ubuntu8_all.deb) ...
Segmentation fault (core dumped)
dpkg: warning: subprocess old pre-removal script returned error exit status 139
dpkg - trying script from the new package instead ...
Segmentation fault (core dumped)
dpkg: error processing /var/cache/apt/archives/python-aptdaemon.pkcompat_0.43+bzr805-0ubuntu8_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 139
No apport report written because MaxReports is reached already
                                                              Segmentation fault (core dumped)
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 139
Preparing to replace python-aptdaemon.gtk3widgets 0.43+bzr805-0ubuntu7 (using .../python-aptdaemon.gtk3widgets_0.43+bzr805-0ubuntu8_all.deb) ...
Segmentation fault (core dumped)
dpkg: warning: subprocess old pre-removal script returned error exit status 139
dpkg - trying script from the new package instead ...
Segmentation fault (core dumped)
dpkg: error processing /var/cache/apt/archives/python-aptdaemon.gtk3widgets_0.43+bzr805-0ubuntu8_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 139
No apport report written because MaxReports is reached already
                                                              Segmentation fault (core dumped)
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 139
Preparing to replace python-aptdaemon 0.43+bzr805-0ubuntu7 (using .../python-aptdaemon_0.43+bzr805-0ubuntu8_all.deb) ...
Segmentation fault (core dumped)
dpkg: warning: subprocess old pre-removal script returned error exit status 139
dpkg - trying script from the new package instead ...
Segmentation fault (core dumped)
dpkg: error processing /var/cache/apt/archives/python-aptdaemon_0.43+bzr805-0ubuntu8_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 139
No apport report written because MaxReports is reached already
                                                              Segmentation fault (core dumped)
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 139
Errors were encountered while processing:
 /var/cache/apt/archives/python-aptdaemon.pkcompat_0.43+bzr805-0ubuntu8_all.deb
 /var/cache/apt/archives/python-aptdaemon.gtk3widgets_0.43+bzr805-0ubuntu8_all.deb
 /var/cache/apt/archives/python-aptdaemon_0.43+bzr805-0ubuntu8_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

The following is also returned when I

sudo tail /var/log/apt/term.log|tr \\r \\n
dpkg: error processing /var/cache/apt/archives/python-aptdaemon_0.43+bzr805-0ubuntu8_all.deb (--unpack):

 subprocess new pre-removal script returned error exit status 139

Segmentation fault (core dumped)

dpkg: error while cleaning up:

 subprocess installed post-installation script returned error exit status 139

Errors were encountered while processing:

 /var/cache/apt/archives/python-aptdaemon.pkcompat_0.43+bzr805-0ubuntu8_all.deb

 /var/cache/apt/archives/python-aptdaemon.gtk3widgets_0.43+bzr805-0ubuntu8_all.deb

 /var/cache/apt/archives/python-aptdaemon_0.43+bzr805-0ubuntu8_all.deb

Log ended: 2013-03-22  10:04:01


Any suggestions would be helpful please as I am still a newbie
precise 12.04

---

### Post by oldos2er on 2013-03-22
Post moved to its own thread. Please start a new thread rather than "hijacking" someone else's.

---

### Post by cortman on 2013-03-22
Try

```
sudo rm -r /var/cache/apt/archives/*
```

Then run the upgrade again.

---

### Post by oldos2er on 2013-03-22
My apologies to handimanmark and cortman. Please see this thread instead: [http://ubuntuforums.org/showthread.php?t=2128220](http://ubuntuforums.org/showthread.php?t=2128220)

---

