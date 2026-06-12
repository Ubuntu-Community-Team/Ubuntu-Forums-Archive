---
title: "Package Operation Failed - Help!"
date: 2012-01-20
forum: New to Ubuntu
---

### Post by joshdcho on 2012-01-20
Hey guys, so whenever I try to update or install something I have been getting this message:

>installArchives() failed: (Reading database ... 
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
(Reading database ... 242146 files and directories currently installed.)
Removing gparted ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Setting up couchdb-bin (1.0.1-0ubuntu17) ...
useradd: cannot lock /etc/passwd; try again later.
adduser: `/usr/sbin/useradd -d /var/lib/couchdb -g couchdb -s /bin/bash -u 116 couchdb' returned error code 1. Exiting.
dpkg: error processing couchdb-bin (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of desktopcouch:
 desktopcouch depends on couchdb-bin (>= 0.10.0-0ubuntu3); however:
  Package couchdb-bin is not configured yet.
dpkg: error processing desktopcouch (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of desktopcouch-ubuntuone:
 desktopcouch-ubuntuone depends on desktopcouch (= 1.0.8-0ubuntu1); however:
  Package desktopcouch is not configured yet.
dpkg: error processing desktopcouch-ubuntuone (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
Errors were encountered while processing:
 couchdb-bin
 desktopcouch
 desktopcouch-ubuntuone
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)
Setting up couchdb-bin (1.0.1-0ubuntu17) ...
useradd: cannot lock /etc/passwd; try again later.
adduser: `/usr/sbin/useradd -d /var/lib/couchdb -g couchdb -s /bin/bash -u 116 couchdb' returned error code 1. Exiting.
dpkg: error processing couchdb-bin (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of desktopcouch:
 desktopcouch depends on couchdb-bin (>= 0.10.0-0ubuntu3); however:
  Package couchdb-bin is not configured yet.
dpkg: error processing desktopcouch (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of desktopcouch-ubuntuone:
 desktopcouch-ubuntuone depends on desktopcouch (= 1.0.8-0ubuntu1); however:
  Package desktopcouch is not configured yet.
dpkg: error processing desktopcouch-ubuntuone (--configure):
 dependency problems - leaving unconfigured

Apparently its something wrong with couchdb-bin, desktopcouch, and desktopcouch-ubuntuone. Any idea on whats wrong and how to fix this? Thanks!

---

### Post by drmrgd on 2012-01-20
What is the command you're running in the example output below?  The line:

> useradd: cannot lock /etc/passwd; try again later.

suggests that you may have not added sudo in front of whatever you're trying to run, which may be cascading the failure throughout the process.

---

### Post by cortman on 2012-01-20
> **drmrgd said:**
> What is the command you're running in the example output below?

^^ this. Also, you could try the old tricks of

```

sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get install -f

```

and see if that clears things up.

---

