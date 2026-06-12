---
title: "What is the root.disk file?"
date: 2012-07-24
forum: New to Ubuntu
---

### Post by hesson on 2012-07-24
Hi,

I have a 30 GB root.disk file sitting in  /host/ubuntu/disks/root.disk, and I don't know what exactly it does. If all my OS info is stored in this file, does that mean I don't have Ubuntu installed as a standalone legitimate OS? What should I do if I want Ubuntu to be my permanent OS, is there a better way to install than WUBI?

Thanks

---

### Post by oldfred on 2012-07-25
Wubi is a version that runs in one file root.disk inside the Windows NTFS partition and uses the Windows boot loader in the MBR to boot. But once loaded it becomes just like a standard Ubuntu. It is intended for a longer test than a liveCD and allows updates. But running inside the NTFS partition means it still relies on Windows.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?)

---

