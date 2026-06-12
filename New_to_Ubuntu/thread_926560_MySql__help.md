---
title: "MySql  help"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by cheeky_lankan on 2008-09-22
hey could some one please help me ? iam trying to populate these two scripts; one creates 5 tables and the other script populates them .. i have mysql and i ran this script to create the tables for the db name 'factory ' : "mysql factory -u root -p  <create.txt " but it errored on me and gave me this output : [http://paste.ubuntu.com/49190/](http://paste.ubuntu.com/49190/) could some one help me please ?


thank you 

cheeky_lankan

---

### Post by indytim on 2008-09-22
You have a syntax error in your sql statement.  Post the script here for further help -or- debug the query your self by inserting something like:

[PHP]
$sq1="select * from tb1 where id>17";

print '<br>sq1='.$sq1;

[/PHP]

IndyTim

---

