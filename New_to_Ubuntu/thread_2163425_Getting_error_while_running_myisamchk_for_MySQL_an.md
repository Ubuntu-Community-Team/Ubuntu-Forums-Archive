---
title: "Getting error while running myisamchk for MySQL and MariaDB"
date: 2013-07-18
forum: New to Ubuntu
---

### Post by avincent3 on 2013-07-18
Hi Everybody,

While running the myisamchk to receover some crashed tables, i am facing some problems.

After the MySQL 5.5.12 or MariaDB 5.5.30 database service is shutdown, we run a myisamchk on our Product's database tables (*.MYI) and notice the following output:

o “Found block with too small length at n; Skipped” where n is some integer that is generally greater than 0 and can be as large as six or seven digits long
o “Found block that points outside data file at n” where n is some integer that is generally greater than 0 and can be as large as six or seven digits long

This happens even for brand new Product installations where we have a freshly installed, new database.

o What do these error messages really mean?
o Are they indicative of a data integrity with our Product's database?
o Is there a configuration setting we can adjust in the my.cnf configuration file that will eliminate these messages?
o Is it safe to simply disregard these messages?

Please help me on this!!!

Thanks,
Anand

---

