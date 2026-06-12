---
title: "Problem occurring while updating"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by Mapuia Ralte on 2008-08-21
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/dists/feisty/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/dists/feisty/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

    THIS IS A PROBLEM I'M FACING WHILE UPDATING.CAN ANYONE HELP ME?

---

### Post by NewJack on 2008-08-21
First, Go to SYSTEM>ADMINISTRATION>SOFTWARE SOURCES

Second, You will be prompted for your password

Third, Under the UBUNTU SOFTWARE tab, look towards the bottom.  You will see a section that states "Installable from CD-ROM/DVD".  Make sure that the Cdrom with Ubuntu box is unchecked.

Then, hit CLOSE and you will be prompted to reload the sources lists.

Hope this helps you.

Joe

---

