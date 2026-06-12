---
title: "Problems with Update Manager"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by Peterfc on 2008-05-11
Hi All

Since 8.4 was downloaded all has been well all updates went without a hitch untill today. I am getting a message i have pasted below. Could anybody help. 


Thanks for all who read this post


Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.



The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Dell Inspiron 2600 2.6 Celeron  200gb Drive 1gb Ram

---

### Post by diablo75 on 2008-05-11
System>Administration>Software Sources.

Change your server to something other than what's selected right now.  You can either pick a server that's closer to you, or use the "Select Best Server" button to auto-ping them all and pick the one with the fastest response time.

---

### Post by Joeb454 on 2008-05-11
> **diablo75 said:**
> 
Change your server to something other than what's selected right now.  You can either pick a server that's closer to you, or use the "Select Best Server" button to auto-ping them all and pick the one with the fastest response time.

Not quite, you simply need to untick the box that says "use the CD as a software source" (or something along those lines) which as you rightly said, can be found in
> **diablo75 said:**
> System>Administration>Software Sources.

---

