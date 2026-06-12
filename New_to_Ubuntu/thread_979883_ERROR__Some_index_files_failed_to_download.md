---
title: "ERROR:  Some index files failed to download"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by paulstaf on 2008-11-12
I am getting an error when I attempt an update:

.....
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
Fetched 1B in 1s (1B/s)
W: Failed to fetch [http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/Postscript-HP/binary-i386/Packages.gz](http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/Postscript-HP/binary-i386/Packages.gz)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.


I traced this down to this site and it appears that it is looking for a folder called postscript-HP but it can't find it because the HP is in lower case as such:   postscript-hp/ 

Here is the link:  [http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/](http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/)

Not sure how to fix this.

Thanks,
Paul

---

### Post by Sef on 2008-11-12
moved to absolute beginner.

---

