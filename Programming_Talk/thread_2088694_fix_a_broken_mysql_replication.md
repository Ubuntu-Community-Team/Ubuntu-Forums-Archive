---
title: "fix a broken mysql replication"
date: 2012-11-27
forum: Programming Talk
---

### Post by siddharth007 on 2012-11-27
[INDENT] Hi all.I had set up a mysql master-slave replication and somehow it  broke.The master is still up,its the slave side where i need to fix the  things up.After some research on the internet i found out that stopping  the slave and issuing the command  **SET GLOBAL sql_slave_skip_counter=N** (**where N is some number of events) **can fix the replication.I have the following questions:

1 What is the value should i put in place of **N**. Is it the number  of queries which executed on the master since replication broke?? If  so,how can i find out how many queries executed on the master since the  replication broke?

2. Will using **SET GLOBAL.... **and then starting the slave will re-sync the master-slave??

 
Note that i am issuing the SET GLOBAL..... command on the slave only after stopping it(stop slave) [/INDENT] 
     
                [[IMG]http://forums.digitalpoint.com/clear.gif[/IMG]]("http://forums.digitalpoint.com/postings.php?do=bump&t=2599482")

---

