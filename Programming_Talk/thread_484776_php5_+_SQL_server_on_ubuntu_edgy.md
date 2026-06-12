---
title: "php5 + SQL server on ubuntu edgy"
date: 2007-06-26
forum: Programming Talk
---

### Post by Cerealz on 2007-06-26
Hello

I nedd to install mssql server suport in php5 running on Ubuntu edgy.
I haver already installed  php - mssql and php-db.

The mssql_* functions are available but the following errors appear:

Warning: mssql_connect() [function.mssql-connect]: Sybase: Client
message: Server is unavailable or does not exist. (severity 78 ) in
/var/www/EP/BackOffice/new1.php on line 9

Warning: mssql_connect() [function.mssql-connect]: Sybase: Unable to
connect in /var/www/EP/BackOffice/new1.php on line 9

Can anyone give me some clues on how to solve this?!?

Thanks

---

### Post by hmLyons on 2007-06-30
You mentioned mssql functions for PHP which are for Microsoft SQL Server. Do you mean to use MySQL or Microsoft SQL Server?

If you have installed mysql, what happens when you use the [mysql PHP]("http://php.net/manual/en/ref.mysql.php") commands rather than the mssql ones?

---

