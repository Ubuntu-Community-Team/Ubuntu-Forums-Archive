---
title: "Updater Isses"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by Squint1987 on 2008-11-13
Failed to fetch [http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/Packages.gz](http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

Any way to get rid of this issue? I'm running Ibex right now.

Thanks

---

### Post by oldsoundguy on 2008-11-13
did you enable the extra repositories?
[http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)

---

### Post by handydan918 on 2008-11-13
Ya know, a nice alternative to automatix is to drop your computer in the swimming pool while it's powered up....

---

### Post by oldsoundguy on 2008-11-13
> **handydan918 said:**
> Ya know, a nice alternative to automatix is to drop your computer in the swimming pool while it's powered up....

AMEN!!

The only third party installers I have used are Envy and Ubuntuzilla!
(and right now Envy is dead in the water for Intrepid!)

---

### Post by ciscosurfer on 2008-11-13
> **Squint1987 said:**
> Failed to fetch [http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/Packages.gz](http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

Any way to get rid of this issue? I'm running Ibex right now.

ThanksYou're running Intrepid Ibex and you're trying to download a package meant for Edgy Eft.  Either way, Automatix has been toast for a while now.

To get rid of it, you need to modify your **/etc/apt/sources.list** and remove that line or you can go to **System > Administration > Software Sources** and do the same thing.

---

