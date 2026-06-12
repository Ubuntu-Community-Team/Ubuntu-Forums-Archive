---
title: "Retoring a MySQL user assess"
date: 2006-12-13
forum: Programming Talk
---

### Post by theDentist on 2006-12-13
I seem to have lost my 'debian-sys-mant' user and password in the user list of MySQL, anyone know how to get it back   :(

---

### Post by linuchsan on 2006-12-13
mysqld --skip-grant-tables --user=mysql
type mysql and reset your pass.

---

### Post by theDentist on 2006-12-14
Thanks I'll give it a try

---

