---
title: "Ubuntu using over 13GB?"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by Adahn on 2008-05-20
My ubuntu install occupies around 13GB of space on it's partition (the Home folder is an additional 1.5GB).
I've had the install around since Dapper or Edgy IIRC, plus one or two kernels built through kernel check (now using default Hardy).
I don't have many added applications and have gone through the cleanup howto here:  [http://ubuntuforums.org/showthread.php?t=140920&highlight=orphaned](http://ubuntuforums.org/showthread.php?t=140920&highlight=orphaned)

Any other tips to slim the install down?

---

### Post by quelx on 2008-05-20
have you tried baobab (**ALT-F2** > **gksudo baobab**) to see what the largest directories are?  Once you get that you can start narrowing down to the offending files and decide if they are needed or not.

---

### Post by philinux on 2008-05-20
Just use the installed disk usage analyser found in accessories. It uses baobab.

---

### Post by quelx on 2008-05-20
> **philinux said:**
> Just use the installed disk usage analyser found in accessories. It uses baobab.
If it's not run with superuser rights, it will miss the files and directories owned by other users with limited permissions (655 or less) which the normal login can't see.  So I'd suggest using the gksudo method.

---

### Post by Adahn on 2008-05-20
I used 'disk usage analyzer'.

Around 6.5 gigs of space is allocated to 2 old kernels I built (through kernel check) in usr/src.   Can I just delete those if not using them?


edit:
there is another gig of space related to those kernels in 'lib/modules'

---

