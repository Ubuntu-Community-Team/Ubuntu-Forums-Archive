---
title: "mysql server problem:"
date: 2011-11-05
forum: New to Ubuntu
---

### Post by RAJASD on 2011-11-05
i have mysql server. it is not working properly.

for example;

create table employee(first varchar(20),last varchar(20),age number);

ERROR 1064 (42000): You have an error in your SQL syntax check the manual that corresponds to your MySQL server version for the right syntax to use near 'number' at line 1

im getting error in number data type. othr data types are fine.
but i dont see any mistake. if i do it in my friends laptop its executing.

what should b the problem?

---

### Post by lncoll on 2011-11-05
As I know NUMBER is not a valid type in MySql.
There are many numeric types:
timyint, smallint, mediumint, int, bigint...decimal, float, double, real... and more.
In MySql help you can decide what type to use.

---

### Post by cap10Ibraim on 2011-11-05
Try always to read the documentation 
[http://dev.mysql.com/doc/refman/5.5/en/numeric-types.html](http://dev.mysql.com/doc/refman/5.5/en/numeric-types.html)
[http://dev.mysql.com/doc/refman/5.5/en/data-types.html](http://dev.mysql.com/doc/refman/5.5/en/data-types.html)
get the reference manual from [http://dev.mysql.com/doc/](http://dev.mysql.com/doc/)
you will need it

---

### Post by RAJASD on 2011-11-06
> **cap10Ibraim said:**
> Try always to read the documentation 
[http://dev.mysql.com/doc/refman/5.5/en/numeric-types.html](http://dev.mysql.com/doc/refman/5.5/en/numeric-types.html)
[http://dev.mysql.com/doc/refman/5.5/en/data-types.html](http://dev.mysql.com/doc/refman/5.5/en/data-types.html)
get the reference manual from [http://dev.mysql.com/doc/](http://dev.mysql.com/doc/)
you will need it

> **lncoll said:**
> As I know NUMBER is not a valid type in MySql.
There are many numeric types:
timyint, smallint, mediumint, int, bigint...decimal, float, double, real... and more.
In MySql help you can decide what type to use.

as i new to mysql i didt know.
thanks for the help.

---

### Post by lncoll on 2011-11-06
> **RAJASD said:**
> as i new to mysql i didt know.
thanks for the help.

That's the reason of this forum, learn, help, learn and help ;)

---

### Post by RAJASD on 2011-11-07
just one more thing. in mysql date datatype is yy/mm/dd. in india
i need dd/mm/yy. i couldt find anywhere how to convert it.

anyone has any idea?

thanks...

---

### Post by ktrout75 on 2011-11-07
hi RAJASD:

Here's a link to the MySQL forum discussing how to cast dates 'on-the-fly' if you're using PHP:

[http://forums.mysql.com/read.php?35,131559,256536#msg-256536](http://forums.mysql.com/read.php?35,131559,256536#msg-256536)

Here's another pointing out the usefulness of the str_to_date() and date_format() functions, which you can use to read or write dates in any format you choose -- without needing to change the default DATE data type style. 

[http://forums.mysql.com/read.php?35,131559,131608#msg-131608](http://forums.mysql.com/read.php?35,131559,131608#msg-131608)

I was curious (as a PostgreSQL user) how MySQL handles date formatting, to see how two relational databases can differ and how they can be the same. Changing date style in Postgres is a simple configuration change, while casting date/time data can be dicier than it appears to be in MySQL.

Hope the links or function names are of some use.

-rob

---

### Post by RAJASD on 2011-11-09
> **ktrout75 said:**
> hi RAJASD:

Here's a link to the MySQL forum discussing how to cast dates 'on-the-fly' if you're using PHP:

[http://forums.mysql.com/read.php?35,131559,256536#msg-256536](http://forums.mysql.com/read.php?35,131559,256536#msg-256536)

Here's another pointing out the usefulness of the str_to_date() and date_format() functions, which you can use to read or write dates in any format you choose -- without needing to change the default DATE data type style. 

[http://forums.mysql.com/read.php?35,131559,131608#msg-131608](http://forums.mysql.com/read.php?35,131559,131608#msg-131608)

I was curious (as a PostgreSQL user) how MySQL handles date formatting, to see how two relational databases can differ and how they can be the same. Changing date style in Postgres is a simple configuration change, while casting date/time data can be dicier than it appears to be in MySQL.

Hope the links or function names are of some use.

-rob

thanks rob...

---

