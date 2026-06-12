---
title: "Lexmark printer driver hits error part-way through installation"
date: 2012-09-26
forum: New to Ubuntu
---

### Post by Taejix on 2012-09-26
I've very recently switched over to Ubuntu (12.04) from Windows and I'm trying to install my printer. Fortunately, there are 32-Bit linux drivers for it available.

Downloaded it as:
```
lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz
```
I figured out I needed to extract it, which gave me:
```
lexmark-08z-series-driver-1.0-1.i386.deb.sh
```

Trying to run it required the root password, so I had to run it in the terminal with:
```
sudo sh ./lexmark-08z-series-driver-1.0-1.i386.deb.sh
```

Which boots up the installer interface after:
```
Verifying archive integrity... All good.
Uncompressing nixstaller..............................................................
Collecting info for this system...
Operating system: linux
CPU Arch: x86
TRACKING IDENT = 170209
cpu speed = 1603 MHz
ram size = 3024.703125 MB
hd avail = 217056 MB
```

However, every time I try to install it, the installer hits an error part way through and stops.

This error, specifically:
```
Extracting file: printdriver.te
Extracting file: lexmark-08z-series-driver-1.0-1.i386.deb
Extracting file: launcher.c
Extracting file: launcher
Extracting file: lsbrowser
Extracting file: lsusbdevice
Using dpkg installation
=============================
Execute: dpkg -i --force-architecture lexmark-08z-series-driver-1.0-1.i386.deb > /tmp/selfgz6757/pkg/files/dpkg_msgs

dpkg: error processing lexmark-08z-series-driver-1.0-1.i386.deb (--install):
 parsing file '/var/lib/dpkg/tmp.ci/control' near line 9 package 'lexmark-08z-series-driver':
 blank line in value of field 'Description'
Errors were encountered while processing:
 lexmark-08z-series-driver-1.0-1.i386.deb
=============================

=============================
Execute: rm lexmark-08z-series-driver-1.0-1.i386.deb

=============================
***** ERROR REPORT *****
```

I'm not quite sure how to go about fixing this? I hope I've posted the right details, any help would be appreciated.

---

### Post by TCell on 2012-09-30
I am in the same boat as you - Have had such good luck with HW and Ubuntu so far - stupidly assumed the printer would be supported...
According to: [http://www.openprinting.org/printers/manufacturer/Lexmark](http://www.openprinting.org/printers/manufacturer/Lexmark)

the X2670 is a paper weight looks like the Lexmark supplied driver is for Ubuntu 8.04 - I am running 32bit Ubuntu 12.04.

Let me know if you have any luck finding a driver that works! Haven't quite got mine back in the box yet...

---

