---
title: "[SOLVED] Re: AptonCD unable to create backup"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by Liakath on 2008-08-03
Dear Friends,

I have a peculiar problem for which I am unable to find any solution. I am using Ubuntu 8.04.1 with all updates current.

I am trying to backup my downloaded packages through APTONCD, which I had used without any problems earlier. Now it throws up an error message as given in Screen Shot (2) attached. I checked up the space in my different partitions / folders through System Monitor (Screenshot 3).

Space available in / partition is about 3.1 GB
Space available in /home partition is about 5.3 GB
Space available in /media/Media Disk is about 6.9 GB
and the size of the aptoncd is only 1.6 GB.

Anyone who can throw some light on this and help me create the backup aptoncd image in either the /home or /media/Media Disk partition?

Liakath

---

### Post by sh4d0w808 on 2008-08-03
Hmmm... maybe aptoncd requires 2x space for the iso. In this case it looks that U need 1.6 GB x 2, at least 3.2 GB. U do not have this space on your / filesystem, only 3.1 GB.

---

### Post by Liakath on 2008-08-03
Dear sh4d,

> **sh4d0w808 said:**
> Hmmm... maybe aptoncd requires 2x space for the iso. In this case it looks that U need 1.6 GB x 2, at least 3.2 GB. U do not have this space on your / filesystem, only 3.1 GB.

Thank you for the thought. That is why I tried to create in /media/Media Disk which is an NTFS partition which has more than twice the space.

Also I have separate partitions / and /home; /tmp which it refers to is under / partition. May be it is something else I has complaints against.

I even tried purging aptoncd and reinstalling without any improvement.

Liakath

---

### Post by Liakath on 2008-08-03
Dear sh4d,

> **sh4d0w808 said:**
> Hmmm... maybe aptoncd requires 2x space for the iso. In this case it looks that U need 1.6 GB x 2, at least 3.2 GB. U do not have this space on your / filesystem, only 3.1 GB.

Thank you very much. I tried your suggestion by making some more space available in / partition making free space more than twice the size of the aptoncd iso. And aptoncd worked to back up.

Thanks once again.

Liakath

---

### Post by sh4d0w808 on 2008-08-04
Your welcome, dear Liakath, I'm glad to help :D

---

