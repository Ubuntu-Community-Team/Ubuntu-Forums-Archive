---
title: "Mysql command line problem"
date: 2010-11-20
forum: Programming Talk
---

### Post by bubuzzz on 2010-11-20
I have switched from Gui tools to mysql command line recently and got problem with the statements. I want to create the foreign key between tables and the commands run successfully, but after that when i backup the database by using mysqldump, all the "foreign key (`tableA_id`) references tableA (`id`)" line are changed into "key `tableA_id` (`tableA_id`)

Is there anyone knowing this ?

---

### Post by meastwood on 2010-11-20
Not sure if this is your problem or not - difficult to say with no examples of cmd-line statements used.

All I can think of is - did you specify the InnoDB storage engine when you created the keys?

> For storage engines other than InnoDB, MySQL Server parses the FOREIGN KEY syntax in CREATE TABLE statements, but does not use or store it. In the future, the implementation will be extended to store this information in the table specification file so that it may be retrieved by mysqldump and ODBC. At a later stage, foreign key constraints will be implemented for MyISAM tables as well. 

---

### Post by bubuzzz on 2010-11-20
:popcorn: That 's it. Thank you very much.:P. Have a nice weekend

---

