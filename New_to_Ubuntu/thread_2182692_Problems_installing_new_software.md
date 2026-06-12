---
title: "Problems installing new software"
date: 2013-10-22
forum: New to Ubuntu
---

### Post by uhhhnoakes on 2013-10-22
I keep getting errors that installation of new software is not working correctly "Package Operation Failed" but the programs are being installed. For example, I downloaded Chromium and I can now use the application but I'm met with a pop up stating there was an error: 

> installArchives() failed: debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
Selecting previously unselected package libxss1:amd64. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 174928 files and directories currently installed.) 
Unpacking libxss1:amd64 (from .../libxss1_1%3a1.2.2-1_amd64.deb) ... 
Selecting previously unselected package chromium-browser. 
Unpacking chromium-browser (from .../chromium-browser_29.0.1547.65-0ubuntu2_amd64.deb) ... 
Selecting previously unselected package chromium-browser-l10n. 
Unpacking chromium-browser-l10n (from .../chromium-browser-l10n_29.0.1547.65-0ubuntu2_all.deb) ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf-2.index... 
Processing triggers for desktop-file-utils ... 
Processing triggers for gnome-menus ... 
Processing triggers for mime-support ... 
Processing triggers for hicolor-icon-theme ... 
Setting up man-db (2.6.5-2) ... 
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
dpkg: error processing man-db (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Setting up libxss1:amd64 (1:1.2.2-1) ... 
Setting up chromium-browser (29.0.1547.65-0ubuntu2) ... 
Setting up chromium-browser-l10n (29.0.1547.65-0ubuntu2) ... 
Processing triggers for libc-bin ... 
Errors were encountered while processing: 
 man-db 
Error in function:  
Setting up man-db (2.6.5-2) ... 
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
dpkg: error processing man-db (--configure): 
 subprocess installed post-installation script returned error exit status 1 



---

### Post by uhhhnoakes on 2013-10-22
Ok, after scouring the web I came across a post that fixed it... the debconf didn't exist anywhere so I had to create the directory: > sudo mkdir /var/cache/debconf this seems to have resolved the issue, from what I can tell. Anyone who could shed some light on why this happend, I would appreciate it. I'm very limited in my understanding of Ubuntu and am learning as I go. Thanks so much!

---

### Post by ibjsb4 on 2013-10-22
> debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 

That is odd since the above indicates debconf does indeed exist.

---

