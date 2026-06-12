---
title: "Changing CD Repository"
date: 2005-12-27
forum: Repositories &amp; Backports
---

### Post by salem7 on 2005-12-27
I want to install some packages from the CD repository but the system checks for the ubuntu CD in *cdrom0*. What changes shall i do to inform the system to search *cdrom1* instead of *cdrom0* ? Thank you in advance.

---

### Post by az on 2005-12-27
Good question.  By default, the cd repositories use the same device as the install cd.

Have you added hardware?  If so, you need to ajdust your /etc/fstab to make the mount point the correct one.

---

