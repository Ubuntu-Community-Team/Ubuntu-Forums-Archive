---
title: "Compiling Nautilus against Tracker for tagging"
date: 2008-07-18
forum: Packaging and Compiling Programs
---

### Post by derubermensch on 2008-07-18
I've attempted to compile and install Nautilus with tracker integration so that I could tag files from the file manager.  I downloaded the tarball of of Nautilus 2.22.5 installed on 8.04.1 and successfully configured and make'd (with the caveat of having to install the headers to libeel2 and tracker), but when I came to checkinstall (I want to be able to remove compiled packages sanely), I came up against the error from checkinstall's log:
> dpkg - warning: downgrading nautilus from 1:2.22.3-0ubuntu2 to 2.22.5-1.
(Reading database ... 110701 files and directories currently installed.)
Preparing to replace nautilus 1:2.22.3-0ubuntu2 (using .../nautilus_2.22.5-1_i386.deb) ...
Unpacking replacement nautilus ...
dpkg: nautilus: warning - conffile `etc/gconf' is not a plain file or symlink (= `/etc/gconf')
dpkg: nautilus: warning - conffile `etc/gconf/gconf.xml.defaults' is not a plain file or symlink (= `/etc/gconf/gconf.xml.defaults')
dpkg: dependency problems prevent configuration of nautilus:
 nautilus-sendto (0.13.2-0ubuntu1) breaks nautilus (<< 1:2.21.2) and is installed.
  Version of nautilus to be configured is 2.22.5-1.
 libeel2-2 (2.22.2-0ubuntu1) breaks nautilus (<= 1:2.21.90) and is installed.
  Version of nautilus to be configured is 2.22.5-1.
dpkg: error processing nautilus (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nautilus


Could someone give me a hand with this?

---

