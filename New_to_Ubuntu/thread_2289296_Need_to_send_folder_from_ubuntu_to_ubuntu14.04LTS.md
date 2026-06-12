---
title: "Need to send folder from ubuntu to ubuntu14.04LTS"
date: 2015-08-03
forum: New to Ubuntu
---

### Post by shajiuddinsegmail on 2015-08-03
Hi All,

Under ubuntu using cron job I am creating mysql database backup which is saving under a folder "db_backup"

I need to create a scheduler which can send this folder "db_backup" from ubuntu (IP: 192.168.220.147) to another ubuntu (IP: 192.168.220.148)

I tried to do this by using scp command but when I enter correct password than it shows me permission denied error

> scp -r root@192.168.220.148:/db_backup /db_backup/
> root@192.168.220.148's password: 
Permission denied, please try again.

If I will able to successfully send file from ubuntu (IP: 192.168.220.147) to another ubuntu (IP: 192.168.220.148) than I will create a cron job for it

Any help will be highly appreciable


Regards

---

### Post by SeijiSensei on 2015-08-03
Use keys to avoid password authentication: [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

