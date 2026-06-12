---
title: "Installation problems"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by Me+ on 2008-07-13
Hi

Im trying to install deluge-torrent from a .deb file, i get the following errors

> Selecting previously deselected package deluge-torrent.
(Reading database ... 76441 files and directories currently installed.)
Unpacking deluge-torrent (from deluge-torrent_0.5.9.3-1_i386.hardy.deb) ...
dpkg: dependency problems prevent configuration of deluge-torrent:
 deluge-torrent depends on dbus-x11; however:
  Package dbus-x11 is not installed.
 deluge-torrent depends on libboost-date-time1.34.1 (>= 1.34.1-2.1); however:
  Package libboost-date-time1.34.1 is not installed.
 deluge-torrent depends on libboost-filesystem1.34.1 (>= 1.34.1-2.1); however:
  Package libboost-filesystem1.34.1 is not installed.
 deluge-torrent depends on libboost-thread1.34.1 (>= 1.34.1-2.1); however:
  Package libboost-thread1.34.1 is not installed.
 deluge-torrent depends on libc6 (>= 2.4); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.4.
 deluge-torrent depends on libgcc1 (>= 1:4.1.1-21); however:
  Version of libgcc1 on system is 1:4.0.3-1ubuntu5.
 deluge-torrent depends on libssl0.9.8 (>= 0.9.8f-1); however:
  Version of libssl0.9.8 on system is 0.9.8a-7ubuntu0.5.
 deluge-torrent depends on libstdc++6 (>= 4.2.1-4); however:
  Version of libstdc++6 on system is 4.0.3-1ubuntu5.
 deluge-torrent depends on python (>= 2.5); however:
  Version of python on system is 2.4.2-0ubuntu3.
 deluge-torrent depends on python-dbus; however:
  Package python-dbus is not installed.
 deluge-torrent depends on python-notify; however:
  Package python-notify is not installed.
 deluge-torrent depends on python-support (>= 0.7.1); however:
  Version of python-support on system is 0.1.1ubuntu1.
 deluge-torrent depends on python2.5; however:
  Package python2.5 is not installed.
 deluge-torrent depends on zlib1g (>= 1:1.2.3.3.dfsg-1); however:
  Version of zlib1g on system is 1:1.2.3-6ubuntu4.
dpkg: error processing deluge-torrent (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 deluge-torrent


From the best i can tell stuff isnt installed and stuff is out of date. How do i upgrade the packages i have.

Also it says it depends on dbus-x11 however when i try to install this it says the package conflicts with dbus. How do  i fix this?

Thanks

---

### Post by hyper_ch on 2008-07-13
why don't you install deluge from the repos?

---

### Post by paulderol on 2008-07-13
+1.

the repository files are older, but certain, and stable.

---

### Post by bumanie on 2008-07-13
I always get the .deb from the deluge site and never had an issue with it. If you went there and are having issues, just use the one from the repositories.

---

### Post by Me+ on 2008-07-13
What repo is it in?

> apt-get install deluge-torrent
Reading package lists... Done
Building dependency tree... Done
Package deluge-torrent is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package deluge-torrent has no installation candidate


Also this could be a problem as private trackers ban older versions of clients.

Have you not got any idea why my .deb installation failed?

---

### Post by bumanie on 2008-07-13
This should do it. Put the code into terminal.> sudo apt-get install delugeAs long as you have enabled the repositories, that should work.

---

### Post by Me+ on 2008-07-13
Oh yeah maybe this is important.

Im running ubuntu server

---

