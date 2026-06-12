---
title: "replacing a different distro"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by gj_clt on 2008-05-25
My son has been using pclos but now wants to move to ubuntu. He has a root partition, swap and home partitions. Can we keep his current home partition and the data on it- mostly pdf files, open office and music- or is it best to completely reformat(having made a dvd back-up of these files).

---

### Post by saj0577 on 2008-05-25
Back them up anyway as back ups are always a good idea no matter what. But if the home partitions is seperate then just leave it and isntall over the top. But make sure in your new partition table your home partition is stil there.

Saj

---

### Post by Patb on 2008-05-25
I would just add this to saj0577's advice.  During install, you should choose manual partitioning and ensure that the /home partition is **not** going to be formatted.  The only partitions you need to format will be root and swap.  

Cheers, Pat.

---

### Post by gj_clt on 2008-05-25
Thanks. This is what I thought. Backups done will finish the job later today.

---

### Post by mbaker824 on 2008-05-25
> **gj_clt said:**
> My son has been using pclos but now wants to move to ubuntu. He has a root partition, swap and home partitions. Can we keep his current home partition and the data on it- mostly pdf files, open office and music- or is it best to completely reformat(having made a dvd back-up of these files).

As someone else said, when you install use manual partitioning, retain the current partitions, and make sure the home partition is NOT selected for formatting.

The only potential gotcha is that different distros may use different user ID ranges - for example, Fedora starts user accounts with user ID 500, while Ubuntu starts with 1000.  When I installed Ubuntu using a Fedora-generated home partition, it set up my primary account OK, but retained the Fedora user ID of 500, which caused some odd problems here and there.  I ended up creating a new account attached to that directory, then deleting the old one, after which I had to chown, chgrp, and chmod to change owner, group, and permissions throughout the home directory.

Good luck,
Mark

---

