---
title: "mysql backup"
date: 2012-05-13
forum: New to Ubuntu
---

### Post by bill-lancaster on 2012-05-13
Have recently switched from slqite to mysql.
Although I've set up the server on my harddrive I can't see where the data is.
I want to maintain a backup on a second harddrive.
Any help would be appreciated.

Ubuntu 12.04, KDE 4.8.1

---

### Post by Hilgo on 2012-05-13
The default database location is /var/lib/mysql iirc.
I prefer to use mysqldump (sudo mysqldump -u USER -pPASSWORD --all-databases ) to make backups though.

---

### Post by Steve R. on 2012-05-26
Apparantly, in my case, the location of the MYSQL database has been "***migrated***" to another location. The *"my.cnf"* file has the expected line: "*datadir= /var/lib/mysql*", but the database files are not there. The direcory "*/var/lib/mysql*" has a little "**x**" in it.  I suspect that the database files may have been migrated as I have loaded PHPAdmin and Apache. 

The reason for my question is that I just loaded "*simple backup*" and wanted to use that opportunity to back-up the database tables.

I will also be looking into Hildago's suggestion:"*to use mysqldump (sudo mysqldump -u USER -pPASSWORD --all-databases) to make backups though.*" 

Would still be good to know were these files are hiding.

---

