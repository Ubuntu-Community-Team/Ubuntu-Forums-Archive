---
title: "failed message while updating to newest ubuntu"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by secuono on 2008-11-28
i get this message while trying to update to the newest ubuntu.

W:Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, E:Some index files failed to download, they have been ignored, or old ones used instead.

why? how can i fix it and update?

---

### Post by Xiong Chiamiov on 2008-11-29
You have the CD listed as a repository to download packages from.  Since you probably want to have updated packages, and not have to have the CD inserted all the time, you need to edit your source list
```

gksudo gedit /etc/apt/sources.list

```
and remove the first line or two, that mention the cdrom.

After that, you will want to
```

sudo apt-get update && sudo apt-get safe-upgrade

```

---

