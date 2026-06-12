---
title: "[SOLVED] how do I remove these files"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by lincoln32 on 2008-06-03
new to ubuntu and tried to get win mobile synce to work (gave up for now)
now when i run update manager I get these 
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/dists/hardy/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/dists/hardy/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by forestpixie on 2008-06-03
open software sources in admin menu - disable the cdrom and close, reload when aasked.

---

### Post by sayakb on 2008-06-03
Goto System->Administration->Software Sources and click on *Third party software* tab. From there, **uncheck** available CD-ROM entries.

EDIT: Whoa.. that was close!

---

### Post by aysiu on 2008-06-03
> **forestpixie said:**
> open software sources in admin menu - disable the cdrom and close, reload when aasked.
Translation:

System > Administration > Software Sources

The CD-ROM source will have a checkbox next to it. Uncheck that box.

---

