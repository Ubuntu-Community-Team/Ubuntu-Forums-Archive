---
title: "MySQL restore problem: tables don't exist"
date: 2012-08-15
forum: New to Ubuntu
---

### Post by whoknewbuntu on 2012-08-15
Last week I was handed a crashed server which had been running MySQL.  In order to resurrect it, I repartitioned the drives, installed Server 12.04, installed mysql-server, and change the configuration back.  Acess to MySQL is restored.

However, I can't seem to recover my database.  The only backup I have is a tar archive of the pre-crash server.  All the mysql files are there, but if I copy the folder for the database into the /var/lib/mysql, I can see the tables with SHOW TABLES, but if I try queries on them, mysql says the tables don't exist.  Actually, there are some tables which use MyISAM, and those tables are fine, but the important tables are all InnoDB, with no associated .idb files.  If I copy the 3 ib* files into /var/lib/mysql, then I can't start mysql any more.

mysqldump and mysqlchk also report that the tables don't exist.

Does anyone know how I can recover my data from the old files?

---

