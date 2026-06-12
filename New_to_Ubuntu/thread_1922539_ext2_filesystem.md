---
title: "ext2 filesystem"
date: 2012-02-09
forum: New to Ubuntu
---

### Post by openation1 on 2012-02-09
how can i partition sda1 to be ext2 instead of ext4 ?

---

### Post by Hendronicus on 2012-02-09
If I might ask, why?

---

### Post by Bodsda on 2012-02-09
Use gparted. Like you would if you were formatting any other volume.
It will destroy all the data first

Bodsda

---

### Post by Paqman on 2012-02-09
> **Hendronicus said:**
> If I might ask, why?

This is a fair question, btw. Why do you think you need ext2?

---

### Post by openation1 on 2012-02-09
well I think is faster than ext4 filesystem is in it?  I did that with slackware I partition primary sda1, to boot and the second one sda2 with ext4 filesystem plus sd5 for swap files.

---

### Post by Paqman on 2012-02-10
> **openation1 said:**
> well I think is faster than ext4 filesystem is in it?

No. It's also lacks journalling, which is a very useful feature for the integrity of your data. Just use ext4.

Also, you don't normally need a /boot partition unless you are doing something a bit unusual with your setup.

---

