---
title: "access rights errror when migrating mysql database from old hard drive"
date: 2017-06-25
forum: New to Ubuntu
---

### Post by togarha on 2017-06-25
Hi,

I´m trying to migrate a mysql database from an old drive which had fedora9 (which did not boot anymore) to an ubuntu.

I copied the /var/lib/mysql folder from the old system to /testdb/mysql in the new system.

I change the owner to mysql:mysql to the new folder and update datadir of my.conf to this new folder, but the mysql server does not boot anymore. I get the following error:
```

170625 12:44:37 [Warning] Using unique option prefix myisam-recover instead of myisam-recover-options is deprecated and will be removed in a future release. Please use the full name instead.
170625 12:44:37 [Note] Plugin 'FEDERATED' is disabled.
/usr/sbin/mysqld: Table 'mysql.plugin' doesn't exist
170625 12:44:37 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
170625 12:44:37 InnoDB: The InnoDB memory heap is disabled
170625 12:44:37 InnoDB: Mutexes and rw_locks use GCC atomic builtins
170625 12:44:37 InnoDB: Compressed tables use zlib 1.2.8
170625 12:44:37 InnoDB: Using Linux native AIO
170625 12:44:37 InnoDB: Initializing buffer pool, size = 128.0M
170625 12:44:37 InnoDB: Completed initialization of buffer pool
170625 12:44:37  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'open'.
InnoDB: Cannot continue operation.
170625 12:44:38 [Warning] Using unique option prefix myisam-recover instead of myisam-recover-options is deprecated and will be removed in a future release. Please use the full name instead.
170625 12:44:38 [Note] Plugin 'FEDERATED' is disabled.
/usr/sbin/mysqld: Table 'mysql.plugin' doesn't exist
170625 12:44:38 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
170625 12:44:38 InnoDB: The InnoDB memory heap is disabled
170625 12:44:38 InnoDB: Mutexes and rw_locks use GCC atomic builtins
170625 12:44:38 InnoDB: Compressed tables use zlib 1.2.8
170625 12:44:38 InnoDB: Using Linux native AIO
170625 12:44:38 InnoDB: Initializing buffer pool, size = 128.0M
170625 12:44:38 InnoDB: Completed initialization of buffer pool
170625 12:44:38  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'open'.
InnoDB: Cannot continue operation.
170625 12:44:38 [Warning] Using unique option prefix myisam-recover instead of myisam-recover-options is deprecated and will be removed in a future release. Please use the full name instead.
170625 12:44:38 [Note] Plugin 'FEDERATED' is disabled.
/usr/sbin/mysqld: Table 'mysql.plugin' doesn't exist
170625 12:44:38 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
170625 12:44:38 InnoDB: The InnoDB memory heap is disabled
170625 12:44:38 InnoDB: Mutexes and rw_locks use GCC atomic builtins
170625 12:44:38 InnoDB: Compressed tables use zlib 1.2.8
170625 12:44:38 InnoDB: Using Linux native AIO
170625 12:44:38 InnoDB: Initializing buffer pool, size = 128.0M
170625 12:44:38 InnoDB: Completed initialization of buffer pool
170625 12:44:38  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'open'.
InnoDB: Cannot continue operation.


```

I tried to change all permissions, even 777 to all files (only to try it), but always have the same result.

How can I recover the databases?

Thanks in advance,

---

### Post by TheFu on 2017-06-28
The normal way to migrate DBs to ensure full compatibility is by dumping the DB, moving that dump file and restoring it in the new system.
[https://www.digitalocean.com/community/tutorials/how-to-migrate-a-mysql-database-between-two-servers](https://www.digitalocean.com/community/tutorials/how-to-migrate-a-mysql-database-between-two-servers) has more details.

[https://dba.stackexchange.com/questions/174/how-can-i-move-a-database-from-one-server-to-another](https://dba.stackexchange.com/questions/174/how-can-i-move-a-database-from-one-server-to-another) has some other options, but there is a key section about binary compatibility between systems that would be important to read.

---

### Post by Habitual on 2017-06-28
[https://serverfault.com/questions/8860/how-can-i-export-the-privileges-from-mysql-and-then-import-to-a-new-server](https://serverfault.com/questions/8860/how-can-i-export-the-privileges-from-mysql-and-then-import-to-a-new-server)

---

