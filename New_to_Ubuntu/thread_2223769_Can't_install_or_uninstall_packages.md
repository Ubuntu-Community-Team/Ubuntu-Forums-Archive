---
title: "Can't install or uninstall packages"
date: 2014-05-12
forum: New to Ubuntu
---

### Post by dave117 on 2014-05-12
I'm a Unix noob so struggling a bit with the commands. Managed to set up SABnzb, Sickbeard and Couch Potato and aall working nicely
I have a problem with Ubuntu 12.04 server. When trying to upgrade or install any package it errors and fails as below
```
Now updating apache2-utils .. 
Installing package(s) with command apt-get -y install apache2-utils .. 
Reading package lists... 
Building dependency tree... 
Reading state information...
The following packages will be REMOVED: openmediavault-omvextrasorg
The following packages will be upgraded: apache2-utils
1 upgraded, 0 newly installed, 1 to remove and 12 not upgraded. 1 not fully installed or removed.
Need to get 0 B/91.4 kB of archives. After this operation, 337 kB disk space will be freed.
(Reading database ... 120507 files and directories currently installed.) 
Removing openmediavault-omvextrasorg ... /var/lib/dpkg/info/openmediavault-omvextrasorg.postrm: 23: .: 
Can't open /etc/default/openmediavault
dpkg: error processing openmediavault-omvextrasorg (--remove): subprocess installed post-removal script returned error exit status 2 
Errors were encountered while processing: openmediavault-omvextrasorg E: Sub-process /usr/bin/dpkg returned an error code (1) .. install failed!
No packages were installed. Check the messages above for the cause of the error. <- Return to package list
```
(This is from Webmin but same result if using Putty or direct on machine)
I have an HP Microserver N54L with 8Gig RAM

---

### Post by WoodenWalker on 2014-05-12
Did you run the install commands with the prefix "sudo" in order to have proper privileges?

---

