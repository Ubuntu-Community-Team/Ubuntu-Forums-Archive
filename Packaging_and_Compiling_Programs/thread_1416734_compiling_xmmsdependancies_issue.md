---
title: "compiling xmms/dependancies issue"
date: 2010-02-26
forum: Packaging and Compiling Programs
---

### Post by rixtr66 on 2010-02-26
im trying to compile xmms.but at ./configure i get an error
[CODE]checking for GLIB - version >= 1.2.2... no
*** Could not run GLIB test program, checking why...
*** The test program compiled, but did not run. This usually means
*** that the run-time linker is not finding GLIB or finding the wrong
*** version of GLIB. If it is not finding GLIB, you'll need to set your
*** LD_LIBRARY_PATH environment variable, or edit /etc/ld.so.conf to point
*** to the installed location  Also, make sure you have run ldconfig if that
*** is required on your system
***
*** If you have an old version installed, it is best to remove it, although
*** you may also be able to get things to work by modifying LD_LIBRARY_PATH
***
*** If you have a RedHat 5.0 system, you should remove the GTK package that
*** came with the system with the command
***
***    rpm --erase --nodeps gtk gtk-devel
configure: error: *** GLIB >= 1.2.2 not installed - please install first ***
rick@ubuntu:~/Desktop/xmms-1.2.11$ 
/CODE]
however i have it installed,i did some research and discovered
i need the Glib-dev package,but im not sure what version
of glib i have.so ineed to know how to find out what version of glib i have.and what Glib-dev package to install.
any help would be appreciated!!
Rick :guitar:

---

### Post by mc4man on 2010-03-01
If you wish to build xmms you need 5 librairies, all available in jaunty or eariler  repo's ( jaunty's can be installed on karmic

[libglib1.2ldbl]("http://packages.ubuntu.com/en/jaunty/libglib1.2ldbl") 
[libglib1.2-dev]("http://packages.ubuntu.com/en/jaunty/libglib1.2-dev")

[libgtk1.2-common]("http://packages.ubuntu.com/en/jaunty/libgtk1.2-common")
[libgtk1.2]("http://packages.ubuntu.com/en/jaunty/libgtk1.2")
[ libgtk1.2-dev]("http://packages.ubuntu.com/en/jaunty/libgtk1.2-dev")
Installed in above listed  order (links are jaunty/karmic

Or if you wish a pre-built with install deps [URL="http://www.pvv.ntnu.no/~knuta/xmms/"]see here
[/URL]

Plugins can be acquired in various ways - search packages.ubuntu, internet and or build

---

