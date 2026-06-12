---
title: "How to switch mount to windows partition from /dev/sda3 to /dev/sda2"
date: 2016-10-17
forum: New to Ubuntu
---

### Post by davycrockett on 2016-10-17
Due to an upgrade to Ubuntu xenial my windows data is on /dev/sda2 instead of /dev/sda3 prior to the upgrade. How do I change nautilus to point to the new location?

Error mounting /dev/sda3 at /media/squirrel/A60C48030C47CD4D: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1001,gid=1001" "/dev/sda3" "/media/squirrel/A60C48030C47CD4D"' exited with non-zero exit status 14: Windows is hibernated, refused to mount.
Failed to mount '/dev/sda3': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

---

### Post by davycrockett on 2016-10-17
Posted in error. Issue solved, partition was still on /dev/sda3

---

### Post by yancek on 2016-10-17
Your problem is explained in the error you posted.  You could not access the windows partition from Ubuntu because you left the system hibernated.  That will probably always happen as Linux won't mount a hibernated partition due to the extremely high change of corruption.

---

### Post by davycrockett on 2016-10-19
> **yancek said:**
> Your problem is explained in the error you posted.  You could not access the windows partition from Ubuntu because you left the system hibernated. 

Actually no I didn't. I shut down the system properly as always.

---

### Post by yancek on 2016-10-19
If you are using windows 8 or 10, the default is to always have hibernation on and you need to shut off hibernation and fast-boot to do a complete shutdown.  So a standard shutdown isn't going to do it.  You neglected to mention which windows you are using so I don't know if you have 8 or 10.  I think the people who write these operating systems know a little more about this than we do and if the error you posted is accurate, that is likely your problem.

---

### Post by davycrockett on 2016-10-19
Firstly I posted that the problem was due to a upgrade of ubuntu implying that there was no problem before the upgrade ie nothing to do with windows settings. Secondly I don't have a problem anymore due to the fact that I marked the thread as solved. I can mount to the windows drive read-only using **sudo mount -t ntfs-3g -o ro /dev/sda3 /media/windows**.

---

