---
title: "MSQL - no primary key? use indexes?"
date: 2010-08-28
forum: Programming Talk
---

### Post by ltwinner on 2010-08-28
I have a drupal module that defines a MYSQL table with 3 columns - node id, comment id and user id - nid, cid, uid.

For this particular module there is no unique value in any of these columns. For example, the table could look like this

nid  cid  uid
0     1    1
0     1    5
1     3    1
2     6    1

As there is no unique value in any column I can't set a primary key on it. I read that you can set a primary key on more than one column and these columns taken together then form a unique primary key. However in my case I can only form a unique key when all three columns are taken together.

One other bit of information is my queries to this table always take the form - "SELECT uid FROM table WHERE nid = x AND cid = y"

With that in mind my questions are -
1. Is there any point to set all of these columns to be primary key? Will it improve performance over having no primary keys?

2. Would setting an index on one or more columns be a good idea here to improve performance? If so, why?

---

### Post by wil on 2010-08-28
I am a MSSQL guy and from that point of view indexes would def be a good thing. If you do not have an index your query would have to do a table scan to make sure it gets all the values. Table scans are bad and you query would get slower and slower as it grows.

I would not do a clustered index as this will degrade inserting data. I would start by putting an index on nid and cid.

I do not think that there is a point to adding a primary key to the table. I would rather considering putting an identity column in if it would be useful. 

The end of the day you need to test, I have noticed that sometimes the query optimizer is clever and sometimes pain stupid.

---

### Post by kalaharix on 2010-08-29
I guess it depends how much data you will be using.

As a matter of course, I frequently do searches on typically 5 characters in a varchar(50) in a 25000 record mySQL database. The varchar(50) is unindexed and I never cease to be amazed at the speed of retrieval. Comes under the heading of: 'How the .... does it do that?'

---

