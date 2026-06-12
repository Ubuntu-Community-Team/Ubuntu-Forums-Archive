---
title: "Problem installing first class client"
date: 2012-01-04
forum: New to Ubuntu
---

### Post by bannesen on 2012-01-04
Hi I'm trying to install first class client from the .deb file that i found on their website. 
 I get this error message (unfortunately in danish)

dpkg: fejl under behandling af /home/bjarke/Skrivebord/fcc-10.014-Linux.i686.deb (--install):
 kan ikke bne filen '/var/lib/dpkg/tmp.ci//.svn': Er et filkatalog
Der opstod fejl under behandlingen:
 /home/bjarke/Skrivebord/fcc-10.014-Linux.i686.deb

**Google translation **
dpkg: error processing / home/bjarke/Skrivebord/fcc-10.014-Linux.i686.deb (- install):
  can not open file '/ var / lib / dpkg / tmp.ci / /. svn': Is a folder
Failures occurred during processing:
  / home/bjarke/Skrivebord/fcc-10.014-Linux.i686.deb

why can't I install this .deb file?

---

### Post by mcduck on 2012-01-04
Based on the information on the web site, the .deb package is made for Debian, not for Ubuntu.

Even though the two distributions have a lot in common, including the package manager, they aren't actually fully compatible and the names of various packages etc. things are different between Debian and Ubuntu.

You'll probably have to use the .tar.gz instead.

---

