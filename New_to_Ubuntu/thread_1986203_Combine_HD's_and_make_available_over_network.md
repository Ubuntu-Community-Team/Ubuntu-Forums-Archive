---
title: "Combine HD's and make available over network?"
date: 2012-05-24
forum: New to Ubuntu
---

### Post by doppel.ganger on 2012-05-24
I have 2 41.1 GB ATA/IDE hard drives. Is there some way I can combine them so they appear as 1 hard drive and make that 1 hard drive available over my network? Thanks!

DG

---

### Post by roelforg on 2012-05-24
How about using an aufs mount and then sharing the mount?

---

### Post by doppel.ganger on 2012-05-24
Ummmmmmmm... Huh?

---

### Post by roelforg on 2012-05-24
> **doppel.ganger said:**
> Ummmmmmmm... Huh?

```

mount -t aufs -o br=/path/to/mounted/drive/1:/path/to/mounted/drive/2 none /mnt/combidrive

```

---

