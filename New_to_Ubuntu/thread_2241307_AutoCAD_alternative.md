---
title: "AutoCAD alternative"
date: 2014-08-25
forum: New to Ubuntu
---

### Post by incarnated623 on 2014-08-25
I am looking for the best Linux alternative to AutoCAD. Price is relative.


Ubuntu 14.04 or even linuxmint 17(either or). Both being 64-bit.


So yep any help would be greatly appreciative.

---

### Post by Frogs Hair on 2014-08-25
I tested the free 2D version a while back, but haven't used AutoCad before . [URL="http://www.3ds.com/products-services/draftsight/overview/"]http://www.3ds.com/products-services/draftsight/overview/

[/URL]http://alternativeto.net/software/autocad/?platform=linux

---

### Post by dave131 on 2014-08-26
I was curious about this myself so I followed the link, downloaded the Ubuntu package, then clicked it and it opened in the software center.  After running for a short while, it errored out with the following:```
Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 255782 files and directories currently installed.) 
Preparing to unpack .../me/Downloads/draftSight.deb ... 
access control disabled, clients can connect from any host 
/var/lib/dpkg/tmp.ci/ShowLicense: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory 
access control enabled, only authorized clients can connect 
dpkg: error processing archive /home/me/Downloads/draftSight.deb (--install): 
 subprocess new pre-installation script returned error exit status 127 
```

It had already asked for my password, so I don't understand if the error is in the package or with permissions or something where it's trying to put things.  That is unless libgtk-x11-2.0.so.0 is a requirement and I don't have it.

Wish I could provide more info but I'm a newbie so this is all I can do for now.

---

### Post by mastablasta on 2014-08-26
seems to be quite clear to me:

> error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory

it needs package libgtk-x11-2.0.so.0  try installing it but make sure you don't fall into some dependency hell (that is I would do this on a test machine or partition or virtualbox).

---

### Post by dave131 on 2014-08-26
Except - it's not found via apt-get, and I looked in Synaptic at all packages with gtk in the name and it's not showing.  So I wouldn't know where to find it.  I'm just on regular Ubuntu 14.04.

---

### Post by dave131 on 2014-08-26
Could not find a download for that lib in my searches on the net, but I did find this:

[http://askubuntu.com/questions/466522/how-to-install-draftsight-on-ubuntu-64bits](http://askubuntu.com/questions/466522/how-to-install-draftsight-on-ubuntu-64bits)

Since I am running 64-bit, I did the recommendation from that link:

sudo apt-get install libuuid1:i386 libice6:i386 libsm6:i386 libxt6:i386 libaudio2:i386 libgtk2.0-0:i386 libcanberra-gtk-module:i386 libcanberra-gtk0:i386 libglu1-mesa:i386

Then reran the install via the software center and all worked then.  There is something in what ever that installs that part of the package contents must be that library.

---

### Post by mastablasta on 2014-08-26
ah yes these are 32bit libraries (packages and meta packages) needed for 64 bit OS to run 32bit apps.

---

