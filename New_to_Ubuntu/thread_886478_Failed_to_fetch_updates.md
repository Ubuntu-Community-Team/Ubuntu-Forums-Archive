---
title: "Failed to fetch updates"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by tidge87 on 2008-08-11
Hi all,

Installed a new CD ROM drive into my PC and now my Ubuntu wont update.

I get this message:

[B]Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.[/B]

I tried to apt-cdrom add with the ubuntu disc but it won't work.

Could somebody please help, thanks.

---

### Post by Elfy on 2008-08-11
If you don't use the cdrom livecd as a source disable it in Software sources - sys - admin menu.

---

### Post by tidge87 on 2008-08-11
Thanks for your help forestpixie! It worked. :popcorn:

---

