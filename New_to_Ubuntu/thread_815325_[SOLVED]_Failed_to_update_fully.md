---
title: "[SOLVED] Failed to update fully"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by jjblackfox on 2008-06-01
Hi, I'm new to linux and I typed sudo apt-get update and I got this error:

W: Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.

How do I fix it? I didn't want to add new CD-Roms, I just wanted to update my system.

---

### Post by HotShotDJ on 2008-06-01
System --> Administration --> Software Sources --> Ubuntu Software
Uncheck "CD-ROM..."

---

### Post by ibuclaw on 2008-06-01
Go into "**System>Administration>Software Sources**" and uncheck the Hardy CD-ROM source.

Then in the terminal.
```
sudo apt-get update
```
will update your repository list and
```
sudo apt-get upgrade
```
will update your system to the most recent app version numbers.

Regards
Iain

---

### Post by jjblackfox on 2008-06-01
> **HotShotDJ said:**
> System --> Administration --> Software Sources --> Ubuntu Software
Uncheck "CD-ROM..."
Thanks for the help, it works now.

---

