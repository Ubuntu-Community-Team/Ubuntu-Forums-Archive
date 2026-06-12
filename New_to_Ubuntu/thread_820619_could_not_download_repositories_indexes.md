---
title: "could not download repositories indexes"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by professorTHC on 2008-06-06
i tried addint the hardy heron repository and when i reload synaptic i get this error message: Could not download repository indexes

Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch [http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/Packages.gz](http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.



any ideas?

---

### Post by avtolle on 2008-06-06
In Software Sources (Under System>>Administration) uncheck the CD as a source. Reload. Then, go to a terminal and edit your sources.list to remove the reference to automatix (or just comment it out with a #). At the terminal, once that has been done```
sudo aptitude update
``` to update your sources list. Hope this helps.

---

### Post by wolfen69 on 2008-06-06
i see you're trying to add the medibuntu repos. no need for that, as you can get everything you need from the regular repos.

---

### Post by sayakb on 2008-06-06
System->Administration->Software sources
There, goto 3rd party software and remove the CDROM entries and the automatix entry.

Also, please do not download packages from Automatix. They often break the system.

---

