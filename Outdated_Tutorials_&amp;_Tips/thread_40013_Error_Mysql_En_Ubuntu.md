---
title: "Error Mysql En Ubuntu"
date: 2005-06-07
forum: Outdated Tutorials &amp; Tips
---

### Post by MDURAND on 2005-06-07
Que tal, al momento de inicar el MySQL en UBUNTU Warty, me arroja este error:

root@ubuntu:/var/run/mysqld # /etc/init.d/mysql start
Starting MySQL database server: mysqld...failed.
Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

Me recomendaron que creara con touch /var/run/mysqld/mysqld.sock y lo "chownee" al mysql...

Hice esto, ya que mysqld.sock no existia; pero al inicar MySQL, me arroja el mismo error; y ademas mysqld.sock desaparece....

No se cual pueda ser el probelma.
Gracias por el apoyo.
Slds

---

