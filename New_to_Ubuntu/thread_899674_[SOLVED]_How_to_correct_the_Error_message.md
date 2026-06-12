---
title: "[SOLVED] How to correct the Error message"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by ellalan on 2008-08-24
Hi
When I try to use the Terminal I get this Error message could someone tell me how to remove it please.
Removing kio-umountwrapper ...
No diversion `diversion of /usr/share/apps/konqueror/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
No diversion `diversion of /usr/share/apps/dolphin/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
Removing `diversion of /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop to /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop.distrib by kio-umountwrapper'
dpkg-divert: error checking `/usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop': No such file or directory
dpkg: error processing kio-umountwrapper (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 kio-umountwrapper
E: Sub-process /usr/bin/dpkg returned an error code (1)
I have previously installed KDE and uninstalled it.
Thank you.

---

### Post by Pro-reason on 2008-08-25
See [http://ubuntuforums.org/showthread.php?p=4786808](http://ubuntuforums.org/showthread.php?p=4786808) and [https://bugs.launchpad.net/ubuntu/+source/kio-umountwrapper/+bug/186729](https://bugs.launchpad.net/ubuntu/+source/kio-umountwrapper/+bug/186729).

---

