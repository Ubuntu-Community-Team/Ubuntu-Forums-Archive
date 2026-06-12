---
title: "Can't install updates."
date: 2008-05-11
forum: New to Ubuntu
---

### Post by 0ni on 2008-05-11
I get the following error while trying to update.

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
```

Failed to fetch cdrom:[Ubuntu-Server 8.04 _Hardy Heron_ - Beta amd64 (20080318.1)]/dists/hardy/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu-Server 8.04 _Hardy Heron_ - Beta amd64 (20080318.1)]/dists/hardy/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

```

Using Ubuntu 64bit server edition with gnome GUI installed. 8.04

---

### Post by HotShotDJ on 2008-05-11
> **0ni said:**
> 
```
Failed to fetch cdrom:[Ubuntu-Server 8.04 _Hardy Heron_ - Beta amd64 (20080318.1)]/dists/hardy/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

```
System --> Administration --> Software Sources.  In the "Ubuntu Software" tab, uncheck "Cdrom with Ubunutu 8.04..." (or some-such) then close.

---

### Post by 0ni on 2008-05-11
Huzzah! Thanks for this. Now to install 1 month's worth of updates lol.

---

