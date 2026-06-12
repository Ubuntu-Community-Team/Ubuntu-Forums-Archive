---
title: "Gdebi and other .deb files error"
date: 2011-10-23
forum: New to Ubuntu
---

### Post by mokman on 2011-10-23
The following erros occur during Gdebi and other deb files installation_
"ubuntu@ubuntu:~$ sudo dpkg -i ~/Downloads/gdebi_0.7.0_all.deb 
Selecting previously deselected package gdebi.
(Reading database ... 136428 files and directories currently installed.)
Unpacking gdebi (from .../Downloads/gdebi_0.7.0_all.deb) ...
dpkg: dependency problems prevent configuration of gdebi:
 gdebi depends on gdebi-core (= 0.7.0); however:
  Package gdebi-core is not installed.
dpkg: error processing gdebi (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 gdebi
ubuntu@ubuntu:~$ ''

>deb packages were in download folder
Commands,"sudo dpkg -i ~/Downloads/gdebi_0.7.0_all.deb "

---

### Post by Elfy on 2011-10-23
You will need to install gdebi-core before you install gdebi.

Not sure what version you're running of ubuntu - but there's a newer version of gdebi in the oneiric repos - so you could install it from the software centre.

0.70 is available in natty.

[http://packages.ubuntu.com/search?keywords=gdebi&suite=default&section=all&arch=any&searchon=names](http://packages.ubuntu.com/search?keywords=gdebi&suite=default&section=all&arch=any&searchon=names)

Edit - if you don't want to install it from there then you can get the dependencies from the packages site.

---

### Post by mokman on 2011-10-23
11.04

Thanks.It worked.Thanks a lot.

---

### Post by sadaruwan12 on 2011-10-23
My dear friend please mark the thread as solved thank you in advance.

---

