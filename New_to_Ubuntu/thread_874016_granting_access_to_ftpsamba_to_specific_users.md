---
title: "granting access to ftp/samba to specific users"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by benfindlay on 2008-07-29
Hi all.

Ive set up samba and proftpd (standalone) and was wondering if there was any way in either program to set access policies on specific sub folders so that certain users can and can't access different folders within the main shares.

For example, I want everyone to access the "public" subfolder, but only want user1 to be able to access the "private" subfolder.

Is this possible with either program?

Cheers

Ben

---

### Post by bab1 on 2008-07-29
Use ACL's.  See [[COLOR="Magenta"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=480218") .  Read response #3

---

### Post by benfindlay on 2008-07-30
Cheers, that looks like exactly what I was looking for!

---

