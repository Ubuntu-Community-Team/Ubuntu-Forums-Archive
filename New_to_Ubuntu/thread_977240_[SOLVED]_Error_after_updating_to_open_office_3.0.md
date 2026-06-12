---
title: "[SOLVED] Error after updating to open office 3.0"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by babloo75 on 2008-11-10
I updated my system with open office 3.0, but after this update, whenever i try updating my computer a new error message appears as follows

Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

How can i remove this/ clear this update error?

One more thing i wanna ask, is open office 3.0 not recognised by ubuntu 8.10, because while updating to open office 3.0 it warned me for possibility of unrecognized software?
and if its so, how can i verify that my computer is not infected by malicious activity/ interference.

Please help........

---

### Post by ad_267 on 2008-11-10
Go to system - administration - software sources - third-party software and untick the cdrom to get rid of that error.

No that warning is just because you are not using an official Ubuntu repository to get OpenOffice 3, there shouldn't be any problems with that as long as you trust the source.

---

### Post by babloo75 on 2008-11-10
thanks dear.

---

