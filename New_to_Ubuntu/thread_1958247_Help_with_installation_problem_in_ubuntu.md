---
title: "Help with installation problem in ubuntu?"
date: 2012-04-13
forum: New to Ubuntu
---

### Post by ryuk200126 on 2012-04-13
I am trying to install sqlmap so I can pentest my website. When I try to 'sudo apt-get install sqlmap' it begins installing but then it fails it says this.
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
No apport report written because the error message indicates its a followup error from a previous failure.
                          Setting up sqlmap (0.6.4-1) ...
Errors were encountered while processing:
 flashplugin-downloader:i386
 flashplugin-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
administrator@ubuntu:~$ 
Any help will be much appreciated.

---

### Post by williejones on 2012-04-13
It appears that flash needs to be installed.  Go to Ubuntu Software Center, search for flash, and install Adobe Flash plugin. Then try your installation again.

---

### Post by mastablasta on 2012-04-14
it is even better to search and install a packge called restricted extras.

---

