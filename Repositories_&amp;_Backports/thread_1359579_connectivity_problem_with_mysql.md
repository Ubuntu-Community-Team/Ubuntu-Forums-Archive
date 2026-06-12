---
title: "connectivity problem with mysql"
date: 2009-12-19
forum: Repositories &amp; Backports
---

### Post by shahin on 2009-12-19
Greetings-
   I am trying to install a rather popular solution that includes snort, mysql, base, php, and apache.  I think I have an issue with the interface between base and mysql.  I know this because I have a number of fields in my database that is populated.  But the fields that are supposed to be populated by base are empty.  I have verified that I can log into the database manually.  Also checked to make sure my username, password, port number, is correct. I made sure 'localhost' is mapped to 127.0.0.1 in the hosts file.  I looked at every log file that seems like it may tell me something.  None of these helped.  Is there any other test you can think of?  Is there a specific log file that may contain information about failed connectivity, and why?  I am able to access the base directory via brawser, and have enough functionality to know the base and php work fine together.  I am lost, please help.

Here is what I mean.  Ideally both of these fields should have the same number of events; at least there should be something on the acid_event. But it is empty.  I can see the number of elements in events increase. But nothing is happening to the other one.
mysql> select count(*) from acid_event;
+----------+
| count(*) |
+----------+
|        0 | 
+----------+
1 row in set (0.00 sec)

mysql> select count(*) from event;
+----------+
| count(*) |
+----------+
|      888 | 
+----------+
1 row in set (0.00 sec)

---

