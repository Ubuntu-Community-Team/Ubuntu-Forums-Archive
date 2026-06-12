---
title: "[SOLVED] Could not download all repository indexes"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by ghostier on 2008-08-21
When i tried to update package information in the update manager. (When i click check in update manager). It gives me this error.
"Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.
"

---

### Post by Ryadt on 2008-08-21
In software sources, uncheck the box for the Cd rom option.

---

### Post by tech9 on 2008-08-21
> **Ryadt said:**
> In software sources, uncheck the box for the Cd rom option.

or you can comment it out by placing a # in your sources.list file under /etc/apt :)

---

### Post by ghostier on 2008-08-21
thanks. solved

---

