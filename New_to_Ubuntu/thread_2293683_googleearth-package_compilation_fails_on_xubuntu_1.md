---
title: "googleearth-package compilation fails on xubuntu 14.04 LTS 64 bit"
date: 2015-09-06
forum: New to Ubuntu
---

### Post by pcrik on 2015-09-06
When I attempt to compile googleearth-package (which I had earlier installed from Ubuntu's repositories), I get this message:

Success! You can now install the package with e.g:

sudo dpkg -i googleearth_6.0.3.2197+1.1.0-1_amd64.deb
-----------------------------
When I attempt to install google-earth, this happens:

~$ sudo dpkg -i googleearth_6.0.3.2197+1.1.0-1_amd64.deb
Selecting previously unselected package googleearth.
(Reading database ... 257641 files and directories currently installed.)
Preparing to unpack googleearth_6.0.3.2197+1.1.0-1_amd64.deb ...
Unpacking googleearth (6.0.3.2197+1.1.0-1) ...
dpkg: dependency problems prevent configuration of googleearth:
 googleearth depends on libcurl3:i386.
 googleearth depends on libsm6:i386.
 googleearth depends on libfontconfig1:i386.
 googleearth depends on libxt6:i386.
 googleearth depends on libxrender1:i386.
 googleearth depends on libxext6:i386.
 googleearth depends on libgl1-mesa-glx:i386.
 googleearth depends on libgl1-mesa-dri:i386.

dpkg: error processing package googleearth (--install):
 dependency problems - leaving unconfigured
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Errors were encountered while processing:
 googleearth


I noticed that there was a file named 'GoogleEarthLinux.bin' in my home directory, and when I changed ownership from root to myself, and chmod a+x'd it, and ran it, this happened:

~$ ./GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 6.0.3.2197.............................................................................................
setup.data/bin/Linux/amd64/setup.gtk2: error while loading shared libraries: libxml2.so.2: cannot open shared object file: No such file or directory
setup.data/bin/Linux/amd64/setup.gtk: error while loading shared libraries: libSM.so.6: cannot open shared object file: No such file or directory
The setup program seems to have failed on amd64

Fatal error, installer failed to run at all!


Any ideas? More to the point, given that I'm out of time to troubleshoot (the task of installing google-earth on xubuntu 14.04 LTS 64 bit having already consumed many hours): does anyone know of an installation method that works? The definition of 'works' must be 'No troubleshooting required -- just works'?



Version info:
e$ cat /etc/*-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.2 LTS"
NAME="Ubuntu"
VERSION="14.04.2 LTS, Trusty Tahr"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 14.04.2 LTS"
VERSION_ID="14.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"

$ lsb_release -a
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:core-4.1-amd64:core-4.1-noarch:cxx-3.0-amd64:cxx-3.0-noarch:cxx-3.1-amd64:cxx-3.1-noarch:cxx-3.2-amd64:cxx-3.2-noarch:cxx-4.0-amd64:cxx-4.0-noarch:cxx-4.1-amd64:cxx-4.1-noarch:desktop-3.1-amd64:desktop-3.1-noarch:desktop-3.2-amd64:desktop-3.2-noarch:desktop-4.0-amd64:desktop-4.0-noarch:desktop-4.1-amd64:desktop-4.1-noarch:graphics-2.0-amd64:graphics-2.0-noarch:graphics-3.0-amd64:graphics-3.0-noarch:graphics-3.1-amd64:graphics-3.1-noarch:graphics-3.2-amd64:graphics-3.2-noarch:graphics-4.0-amd64:graphics-4.0-noarch:graphics-4.1-amd64:graphics-4.1-noarch:languages-3.2-amd64:languages-3.2-noarch:languages-4.0-amd64:languages-4.0-noarch:languages-4.1-amd64:languages-4.1-noarch:multimedia-3.2-amd64:multimedia-3.2-noarch:multimedia-4.0-amd64:multimedia-4.0-noarch:multimedia-4.1-amd64:multimedia-4.1-noarch:printing-3.2-amd64:printing-3.2-noarch:printing-4.0-amd64:printing-4.0-noarch:printing-4.1-amd64:printing-4.1-noarch:qt4-3.1-amd64:qt4-3.1-noarch:security-4.0-amd64:security-4.0-noarch:security-4.1-amd64:security-4.1-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

---

### Post by sandyd on 2015-09-06
dpkg does not install dependencies for a package alternatively.

Running
```

sudo apt-get -f install
```
after getting a error about missing dependencies in dpkg will cause apt-get to attempt to install dependencies.

---

### Post by monkeybrain20122 on 2015-09-06
Not sure why you want to go through the hard way just to install a very old version of GE. Get the .deb from [http://www.google.com/earth/download/ge/agree.html](http://www.google.com/earth/download/ge/agree.html)

---

