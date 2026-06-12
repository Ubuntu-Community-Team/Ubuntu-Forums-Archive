---
title: "How Can I fix this python-daemon dependence?"
date: 2012-11-16
forum: New to Ubuntu
---

### Post by sy373466062 on 2012-11-16
** I types sudo apt-get upgrade , it gives:**```

You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 eog : Depends: shared-mime-info (>= 0.20)
 evince : Depends: shared-mime-info
 kdelibs5-plugins : Depends: shared-mime-info (>= 0.30)
 libfile-mimeinfo-perl : Depends: shared-mime-info
 libgtk-3-0 : Depends: shared-mime-info
 libgtk2-perl : Depends: shared-mime-info
 libgtk2.0-0 : Depends: shared-mime-info
 libgupnp-1.0-4 : Depends: shared-mime-info
 nautilus : Depends: shared-mime-info (>= 0.50)
 python-aptdaemon-gtk : Depends: python-aptdaemon.gtkwidgets (= 0.43+bzr697-0ubuntu1) but 0.43+bzr805-0ubuntu6 is installed
                        Depends: python-aptdaemon.gtk3widgets (= 0.43+bzr697-0ubuntu1) but 0.43+bzr805-0ubuntu5 is installed
 python-aptdaemon.gtk3widgets : Depends: python-aptdaemon (= 0.43+bzr805-0ubuntu5) but 0.43+bzr805-0ubuntu6 is installed
E: Unmet dependencies. Try using -f.
```


so I types
**sudo apt-get install -f :**```


The following packages will be upgraded:
  python-aptdaemon-gtk python-aptdaemon.gtk3widgets
2 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
6 not fully installed or removed.
Need to get 496 kB/513 kB of archives.
After this operation, 2,562 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://mirrors.ustc.edu.cn/ubuntu/](http://mirrors.ustc.edu.cn/ubuntu/) precise-updates/main shared-mime-info amd64 1.0-0ubuntu4.1 [496 kB]
Fetched 496 kB in 1s (391 kB/s)           
Selecting previously unselected package shared-mime-info.
(Reading database ... 221479 files and directories currently installed.)
Unpacking shared-mime-info (from .../shared-mime-info_1.0-0ubuntu4.1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 1 added doc-base file...
dpkg: dependency problems prevent configuration of python-aptdaemon.gtk3widgets:
 python-aptdaemon.gtk3widgets depends on python-aptdaemon (= 0.43+bzr805-0ubuntu5); however:
  Version of python-aptdaemon on system is 0.43+bzr805-0ubuntu6.
dpkg: error processing python-aptdaemon.gtk3widgets (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-aptdaemon-gtk:
 python-aptdaemon-gtk depends on python-aptdaemon.gtkwidgets (= 0.43+bzr697-0ubuntu1); however:
  Version of python-aptdaemon.gtkwidgets on system is 0.43+bzr805-0ubuntu6.
 python-aptdaemon-gtk depends on python-aptdaemon.gtk3widgets (= 0.43+bzr697-0ubuntu1); however:
  Version of python-aptdaemon.gtk3widgets on system is 0.43+bzr805-0ubuntu5.
dpkg: error processing python-aptdaemon-gtk (--configure):
 dependency problems - leaving unconfiguredNo apport report written  because the error message indicates its a followup error from a previous  failure.
                                                                       No apport report written because the error message indicates  its a followup error from a previous failure.

dpkg: dependency problems prevent configuration of landscape-client-ui-install:
 landscape-client-ui-install depends on python-aptdaemon.gtk3widgets; however:
  Package python-aptdaemon.gtk3widgets is not configured yet.
dpkg: error processing landscape-client-ui-install (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on python-aptdaemon.gtk3widgets (>= 0.40) | synaptic; however:
  Package python-aptdaemon.gtk3widgets is not configured yet.
  Package synaptic is not installed.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on update-manager-gnome | update-manager; however:
  Package update-manager-gnome is not installed.
  Package update-manager is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leavingNo apport report written because the error  message indicates its a followup error from a previous failure.
                                                         No apport report written because MaxReports is reached already
                                        No apport report written because MaxReports is reached already
                       No apport report written because MaxReports is reached already
       unconfigured
dpkg: dependency problems prevent configuration of sessioninstaller:
 sessioninstaller depends on python-aptdaemon.gtk3widgets; however:
  Package python-aptdaemon.gtk3widgets is not configured yet.
dpkg: error processing sessioninstaller (--configure):
 dependency problems - leaving unconfigured
Setting up shared-mime-info (1.0-0ubuntu4.1) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Errors were encountered while processing:
 python-aptdaemon.gtk3widgets
 python-aptdaemon-gtk
 landscape-client-ui-install
 update-manager
 update-notifier
 sessioninstaller
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

How can I fix this ?

---

### Post by Aaron Christianson on 2012-11-16
Couple of things:
1. It is normally preferable to post terminal output in ```
 tags.
2. Did you run...
[code]sudo apt-get update
```... before trying to upgrade? Not doing this will almost always case the upgrade to fail, and often causes installs to fail as well. I assume you did this but better to ask, in case you didn't
3. Which version of Ubuntu are you using, 12.04 LTS, 12.10, etc.

edit: looking at the errors, do you have any ppa's, pinned packages, or other external debs installed? If so, this can sometimes lead to what is known as "dependency hell." It looks like you might be in it.

---

### Post by Vim on 2012-11-26
It seems possible to me that I had a related problem in Kubuntu 12.04.  In any case, after I ran Kubuntu's Muon Update Manager, I got the error message:

        (title) Commit error - Muon Update Manager

                   The following errors occurred while
                   applying changes:

                                  Details
             Package: xul-ext-ubufox
             Error: dependency problems - leaving unconfigured

             Package: python-aptdaemon.gtk3widgets
             Error: dependency problems - leaving unconfigured

It seems to me that my problem may be related to that of sy373466062 because mine involves a dependency problem with the python-aptdaemon.gtk3widgets package, while sy373466062's problem involves a python-daemon.

I followed Aaron Christianson's advice to run:

         code:
                   sudo apt-get update

I then ran the Muon Update Manager once again, after which I got the message that my system was now up to date.

---

### Post by newb85 on 2012-11-27
@sy373466062,

The first line of the output you posted contained a very good suggestion.  Try running
```
sudo apt-get update
sudo apt-get -f install
```

---

