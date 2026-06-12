---
title: "Trying to install updates and getting this error"
date: 2013-11-06
forum: New to Ubuntu
---

### Post by rick_c2 on 2013-11-06
The package system is broken

Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f

The following packages have unmet dependencies:

calibre: Depends: python (>= 2.6) but 2.7.3-0ubuntu2.2 is installed
         Depends: python-pypdf (>= 1.10) but 1.13-1 is installed
         Depends: python-cssutils (>= 0.9.6) but 0.9.8-1ubuntu2 is installed
         Depends: python-encutils (>= 0.9.5) but it is a virtual package
         Depends: python-cherrypy3 (>= 3.1.1) but 3.2.2-2 is installed
         Depends: ttf-liberation but it is not installed
         Depends: calibre-bin (>= 0.6.42+dfsg-0ubuntu1) but 0.8.38+dfsg-1 is installed

When i run - apt-get install -f in the Terminal i get:

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Help please

---

### Post by speartip on 2013-11-06
You need to run "sudo apt-get install -f" in a terminal, & make sure any other package manager/update manager is closed.
Also would be helpful to know what version of 'buntu you are using.

---

### Post by grahammechanical on 2013-11-06
Also, what application are you trying to install.  It seems to me that the application depends on libraries that are older than the versions already installed. Can you not install this application through the software Centre? Doing that  can avoid issues like this. Regards.

---

### Post by Linuxratty on 2013-11-06
> **speartip said:**
> You need to run "sudo apt-get install -f" in a terminal, & make sure any other package manager/update manager is closed.
.

 I  had your problem as well and this solved it for me.

---

### Post by rick_c2 on 2013-11-07
Ran "sudo apt-get install -f"

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  calibre-bin python-routes libqt4-test libqt4-designer libchm1 python-lxml
  libpodofo0.9.0 python-cherrypy3 python-dnspython libqt4-help python-qt4
  python-sip python-django calibre python-mechanize python-webob
  python-django-tagging libqtassistantclient4 thunderbird-globalmenu
  python-support libqt4-scripttools libqtwebkit4 python-beautifulsoup
  python-pypdf python-cssutils python-pyparsing
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  calibre
The following packages will be upgraded:
  calibre
1 upgraded, 0 newly installed, 0 to remove and 27 not upgraded.
1 not fully installed or removed.
Need to get 0 B/14.7 MB of archives.
After this operation, 2,861 kB of additional disk space will be used.
Do you want to continue [Y/n]?

---

### Post by rick_c2 on 2013-11-07
12.04

---

### Post by philinux on 2013-11-07
> **rick_c2 said:**
> Ran "sudo apt-get install -f"

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  calibre-bin python-routes libqt4-test libqt4-designer libchm1 python-lxml
  libpodofo0.9.0 python-cherrypy3 python-dnspython libqt4-help python-qt4
  python-sip python-django calibre python-mechanize python-webob
  python-django-tagging libqtassistantclient4 thunderbird-globalmenu
  python-support libqt4-scripttools libqtwebkit4 python-beautifulsoup
  python-pypdf python-cssutils python-pyparsing
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  calibre
The following packages will be upgraded:
  calibre
1 upgraded, 0 newly installed, 0 to remove and 27 not upgraded.
1 not fully installed or removed.
Need to get 0 B/14.7 MB of archives.
After this operation, 2,861 kB of additional disk space will be used.
Do you want to continue [Y/n]?

Hit the Y and enter.

---

### Post by rick_c2 on 2013-11-07
dpkg: dependency problems prevent configuration of calibre:
 calibre depends on python-encutils (>= 0.9.5); however:
  Package python-encutils is not installed.
dpkg: error processing calibre (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 calibre
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by philinux on 2013-11-07
> **rick_c2 said:**
> dpkg: dependency problems prevent configuration of calibre:
 calibre depends on python-encutils (>= 0.9.5); however:
  Package python-encutils is not installed.
dpkg: error processing calibre (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 calibre
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
sudo apt-get purge calibre
```

You can install it again once sytem fixed, also.

```
sudo apt-get autoremove
```

---

### Post by rick_c2 on 2013-11-07
Thank you 

That did it.

---

