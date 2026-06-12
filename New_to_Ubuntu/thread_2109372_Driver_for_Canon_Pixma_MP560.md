---
title: "Driver for Canon Pixma MP560"
date: 2013-01-27
forum: New to Ubuntu
---

### Post by capateke on 2013-01-27
I have downloaded driver for Canon MP560 series but on install command get the following message

Execution command = sudo dpkg -iG ./packages/cnijfilter-common_3.20-1_i386.deb
Selecting previously unselected package cnijfilter-common:i386.
(Reading database ... 220746 files and directories currently installed.)
Unpacking cnijfilter-common:i386 (from .../cnijfilter-common_3.20-1_i386.deb) ...
dpkg: dependency problems prevent configuration of cnijfilter-common:i386:
 cnijfilter-common:i386 depends on libpopt0 (>= 1.7).
dpkg: error processing cnijfilter-common:i386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cnijfilter-common:i386
capateke@capateke-SATELLITE-L850D-12P:~/cnijfilter-mp560series-3.20-1-i386-deb$  

Does this mean the driver is incompatible with Ubuntu 12.04 (x64)? Is there a solution?

---

### Post by deadflowr on 2013-01-27
Yes.
If your system is a 64-bit, then you'll need to install the amd64.deb, and not the i386.deb.
386,686 are 32-bit.
X86_64 and amd64 are 64-bit.

Don't worry about the amd64 naming, it's a trademark thing or something.

---

### Post by capateke on 2013-01-28
Thanks for that info. I followed it up by visiting [www.debian-administration.org/articles/531](www.debian-administration.org/articles/531) (found from a Google search on amd64.deb)which indicated that to get the dependencies needed by the driver for the 64 bit architecture it is necessary to use

apt-get install ia32-libs

which I did. When I tried to install the driver I got the message that it was necessary to install libpopt0. After doing so the driver installed and I followed the on screen instructions to register the printer. Printer and laptop are now wirelessly married and working (although there are some minor issues to sort out. So thanks again for setting me on the right path

---

