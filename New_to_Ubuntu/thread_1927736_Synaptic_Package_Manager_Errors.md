---
title: "Synaptic Package Manager Errors"
date: 2012-02-18
forum: New to Ubuntu
---

### Post by Bonesikr on 2012-02-18
Whenever I try to install a program using synaptic Package Manager I get two error messages, the first is:



```
[B]debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Selecting previously deselected package galaxy.
(Reading database ... 170580 files and directories currently installed.)
Unpacking galaxy (from .../galaxy_1.8-1~getdeb1_amd64.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up man-db (2.6.0.2-2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Setting up liblapack3gf (3.3.1-1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing liblapack3gf (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python-numpy:
 python-numpy depends on liblapack3gf | liblapack.so.3gf | libatlas3gf-base; however:
  Package liblapack3gf is not configured yet.
  Package liblapack.so.3gf is not installed.
  Package liblapack3gf which provides liblapack.so.3gf is not configured yet.
  Package libatlas3gf-base is not installed.
dpkg: error processing python-numpy (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up galaxy (1.8-1~getdeb1) ...
Errors were encountered while processing:
 man-db
 liblapack3gf
 python-numpy
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up man-db (2.6.0.2-2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up liblapack3gf (3.3.1-1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing liblapack3gf (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-numpy:
 python-numpy depends on liblapack3gf | liblapack.so.3gf | libatlas3gf-base; however:
  Package liblapack3gf is not configured yet.
  Package liblapack.so.3gf is not installed.
  Package liblapack3gf which provides liblapack.so.3gf is not configured yet.
  Package libatlas3gf-base is not installed.
dpkg: error processing python-numpy (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 man-db
 liblapack3gf
 python-numpy[/B]
```



And the second is,


[B]An error occurred

The following details are provided:

E: man-db: subprocess installed post-installation script returned error exit status 1
E: liblapack3gf: subprocess installed post-installation script returned error exit status 1
E: python-numpy: dependency problems - leaving unconfigured[/B]


Sometimes the programs will run, other times they wont.


Any help will be appreciated, thanks

---

### Post by MasterNetra on 2012-02-18
"debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable"

Your only running one instance of synaptic package manager right? And your not running the Software center either I hope? Only one package management utlity and once instance of them can be used at one time. Something else is running it seems, if not software center or another instance of synaptic, then it could be a updater. You can't get or install anything while the updater is getting package info, packages, or installing/updating.

---

### Post by Bonesikr on 2012-02-18
Yeah, only one instance of synaptic package manager is running and software manager isn't running. Don't think there is an updater running, would I be able to locate it if there is?

Thanks for the quick reply

---

### Post by sailor2001 on 2012-02-18
system/administration/update manager.  should also see it listed on bottom left panel

---

### Post by donkyhotay on 2012-02-19
If you haven't done so try restarting the computer to close out any processes you may have opened and not closed properly.

//edit: reported the spam already

---

### Post by Bonesikr on 2012-02-19
Everything seems to be working now, think the restart helped.

Thanks for the replies

---

