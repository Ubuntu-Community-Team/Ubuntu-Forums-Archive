---
title: "Can't install...anything?"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by adobrakic on 2008-08-21
salgnsdlgsdg...

> After this operation, 26.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse mozilla-plugin-vlc 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.1 [37.9kB]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse vlc-plugin-esd 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.1 [4876B]
Fetched 42.8kB in 0s (45.5kB/s)            
(Reading database ... 152803 files and directories currently installed.)
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
ado@ado-desktop:~$ 


wtf is kio-umountwrapper? everytime i try to install anything it gives me that error.

---

### Post by cariboo on 2008-08-21
See this bug #186729:

[https://bugs.launchpad.net/ubuntu/+source/kio-umountwrapper/+bug/186729](https://bugs.launchpad.net/ubuntu/+source/kio-umountwrapper/+bug/186729)

Jim

---

