---
title: "Every package I install says it fails, but seems to work."
date: 2011-11-21
forum: New to Ubuntu
---

### Post by ThatKush on 2011-11-21
Hello all,

I've done some searching for this, and haven't found any answers otherwise, so I figured I'd try this route. I just installed Ubuntu 11.10 on my new Sony Vaio. I really enjoyed the first few hours of just browsing around - but when I decided to check out some open source software I've heard about (like GIMP - and other applications I see in the software center). Every single time I try to install a "package" it says it fails. However, if I search for the application, it seems installed and opens up. I think the first to do it was Adobe Flash. Here is the log from "Stellarium" from the software center.

installArchives() failed: Selecting previously deselected package stellarium-data. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 125732 files and directories currently installed.) 
Unpacking stellarium-data (from .../stellarium-data_0.11.0-1_all.deb) ... 
Selecting previously deselected package stellarium. 
Unpacking stellarium (from .../stellarium_0.11.0-1_amd64.deb) ... 
Processing triggers for gnome-menus ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Processing triggers for man-db ... 
Setting up flashplugin-downloader:i386 (11.0.1.152ubuntu1) ... 
Downloading... 
--2011-11-21 17:24:39--  [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.0.1.152.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.0.1.152.orig.tar.gz) 
Resolving archive.canonical.com... 91.189.88.33 
Connecting to archive.canonical.com|91.189.88.33|:80... connected. 
HTTP request sent, awaiting response... 404 Not Found 
2011-11-21 17:24:39 ERROR 404: Not Found. 
 
download failed 
The Flash plugin is NOT installed. 
dpkg: error processing flashplugin-downloader:i386 (--configure): 
 subprocess installed post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of flashplugin-installer: 
 flashplugin-installer depends on flashplugin-downloader (>= 11.0.1.152ubuntu1); however: 
  Package flashplugin-downloader is not installed. 
  Package flashplugin-downloader:i386 is not configured yet. 
dpkg: error processing flashplugin-installer (--configure): 
 dependency problems - leaving unconfigured 
Setting up stellarium-data (0.11.0-1) ... 
No apport report written because the error message indicates its a followup error from a previous failure.
Setting up stellarium (0.11.0-1) ... 
Errors were encountered while processing: 
 flashplugin-downloader:i386 
 flashplugin-installer 
Error in function:  
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1) 
Setting up flashplugin-downloader:i386 (11.0.1.152ubuntu1) ... 
Downloading... 
--2011-11-21 17:24:40--  [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.0.1.152.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.0.1.152.orig.tar.gz) 
Resolving archive.canonical.com... 91.189.88.33 
Connecting to archive.canonical.com|91.189.88.33|:80... connected. 
HTTP request sent, awaiting response... 404 Not Found 
2011-11-21 17:24:41 ERROR 404: Not Found. 
 
download failed 
The Flash plugin is NOT installed. 
dpkg: error processing flashplugin-downloader:i386 (--configure): 
 subprocess installed post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of flashplugin-installer: 
 flashplugin-installer depends on flashplugin-downloader (>= 11.0.1.152ubuntu1); however: 
  Package flashplugin-downloader is not installed. 
  Package flashplugin-downloader:i386 is not configured yet. 
dpkg: error processing flashplugin-installer (--configure): 
 dependency problems - leaving unconfigured 
Errors were encountered while processing: 



Thanks for any help in advance.

---

