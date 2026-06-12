---
title: "Changing Apache root"
date: 2006-05-09
forum: Programming Talk
---

### Post by indytim on 2006-05-09
Title pretty much sums it up.  I'd like to change the root from /var/www
to a different directory.  Do I edit the httpd.conf file to make this happen and/or are there lines to edit in the apache.conf file?

Thanks,

IndyTim

---

### Post by LordHunter317 on 2006-05-09
For Apache2, the DocumentRoot is defined in sites-available/default.  

This is covered in the package documentation in /usr/share/doc/apache2, FWIW.

---

