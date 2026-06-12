---
title: "dpkg dependancy error"
date: 2013-06-01
forum: New to Ubuntu
---

### Post by luyangliuable on 2013-06-01
I'm new to Ubuntu as a user. Furthermore, I ran into an issue associated with upgrading packages, wherein the terminal gave me an error:

sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
10 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up initramfs-tools (0.103ubuntu0.7) ...
update-initramfs: deferring update (trigger activated)
lzma: (stdout): Write error: No space left on device
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-3.8.0-19-generic:
 linux-image-3.8.0-19-generic depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.


dpkg: error processing linux-image-3.8.0-19-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-3.8.0-23-generic:
 linux-image-3.8.0-23-generic depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.


dpkg: error processing linux-image-3.8.0-23-generic (--configure):
 dependency problems - leaving unconfigured
Setting up plymouth-theme-ubuntu-text (0.8.8-0ubuntu6.1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    update-initramfs: deferring update (trigger activated)
lzma: (stdout): Write error: No space left on device
dpkg: error processing plymouth-theme-ubuntu-text (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-extra-3.8.0-23-generic:
 linux-image-extra-3.8.0-23-generic depends on linux-image-3.8.0-23-generic; however:
  Package linux-image-3.8.0-23-generic is not configured yet.


dpkg: error processing linux-image-extra-3.8.0-23-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.8.0-23-generic; however:
  Package linux-image-3.8.0-23-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-3.8.0-23-generic; however:
  Package linux-image-extra-3.8.0-23-generic is not configured yet.


dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.8.0.23.39); however:
  Package linux-image-generic is not configured yet.


dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-extra-3.8.0-19-generic:
 linux-image-extra-3.8.0-19-generic depends on linux-image-3.8.0-19-generic; however:
  Package linux-image-3.8.0-19-generic is not configured yet.


dpkg: error processing linux-image-extra-3.8.0-19-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up plymouth-theme-ubuntu-logo (0.8.8-0ubuntu6.1) ...
update-initramfs: deferring update (trigger activated)
lzma: (stdout): Write error: No space left on device
dpkg: error processing plymouth-theme-ubuntu-logo (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of casper:
 casper depends on initramfs-tools (>= 0.92bubuntu55); however:
  Package initramfs-tools is not configured yet.


dpkg: error processing casper (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 initramfs-tools
 linux-image-3.8.0-19-generic
 linux-image-3.8.0-23-generic
 plymouth-theme-ubuntu-text
 linux-image-extra-3.8.0-23-generic
 linux-image-generic
 linux-generic
 linux-image-extra-3.8.0-19-generic
 plymouth-theme-ubuntu-logo
 casper
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Bashing-om on 2013-06-01
[COLOR=#000000]luyangliuable; Hi ! Welcome to the forum.

The error report advises you of the why and what happened as a result; see:
[/COLOR]> [COLOR=#000000]Setting up initramfs-tools (0.103ubuntu0.7) ...[/COLOR]
[COLOR=#000000]update-initramfs: deferring update (trigger activated)[/COLOR]
[COLOR=#000000]lzma: (stdout): Write error: No space left on device
[/COLOR][COLOR=#000000]
So, as a first small step to see the disk space/usage and a pointer where to look:
post back - between code (#) tags - the output of terminal code:
```

df -h

```
and we can work on getting you some operating room on your system.
[/COLOR][INDENT=2][COLOR=#000000]
small thing can have big head ache

[/COLOR][/INDENT]

---

