---
title: "How to mount windows drives automatically at startup?"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by sharks on 2008-05-21
How to mount windows drives automatically at startup?

---

### Post by dark_harmonics on 2008-05-21
you need to put an entry for them into your /etc/fstab. First find out what the device name is with sudo fdsik -l The device name will be the entry with NTFS next to it.

use that to put an entry into the /etc/fstab something like:

/dev/sda /media/mountpoint ntfs-3g defaults 0 0

Edit:

Code from [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009) that is relevant to the fstab entry:
/dev/<your partition>     /media/<mount point>     ntfs-3g     defaults,locale=en_US.utf8   0    0

---

