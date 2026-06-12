---
title: "[SOLVED] Different mount points"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by faytaliti on 2008-05-21
what are the differences between the various mount points like /home, /usr , /var, etc...:confused:

---

### Post by NightwishFan on 2008-05-21
Those are directories. I believe there might be some performance benefit to having them on different partitions but I have never noticed anything so I use only 1 ext3 partition and 1 swap. /home is the user files /boot is boot files and /tmp is temporary files.

---

### Post by Maestro23 on 2008-05-21
Should shed some light for ya: [http://www.linuxcommand.org/lts0040.php](http://www.linuxcommand.org/lts0040.php)

---

### Post by faytaliti on 2008-05-21
what difference does it make to mount a hard disk on each of these locations :confused:

---

### Post by RequinB4 on 2008-05-21
> **faytaliti said:**
> what difference does it make to mount a hard disk on each of these locations :confused:

None, really, except for "just" organization.  Your mount point is simply where you are telling the file system to create a link to your new hardware  Consider if you have a file cabinet with all of the files arranged in haphazard folders unorganized.  It would be an utter mess to find stuff.

In general stick with /media/FOLDER/ if you're custom-mounting things.

---

