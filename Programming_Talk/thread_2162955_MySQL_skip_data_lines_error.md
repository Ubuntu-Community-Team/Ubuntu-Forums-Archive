---
title: "MySQL skip data lines error"
date: 2013-07-16
forum: Programming Talk
---

### Post by jll339 on 2013-07-16
Hi all,

I'm having a very odd error with MySQL and trying to load data into my DB.

```
DATA LOCAL INFILE '/directory/path/refid.csv' INTO TABLE tomato_il.refid;
```

The message then is as follows:
```
Query OK, 8 rows affected, 65535 warnings (4.29 sec)
Records: 575880  Deleted: 0  Skipped: 575872  Warnings: 104201
```

So out of **575,880** rows of data, only **8** were loaded into the table! >.<

I tripled check and then checked again to make sure that all of the data is 'legal' according to my schema (ex: numeric/character types, size parameters, etc...). Everything is fine.

The only weird thing that was in the file was that had '###' between different "groups" I guess you could say. So it would be like:

col1 col2 col3    [tab delimited]
col1 col2 col3 
col1 col2 col3 
col1 col2 col3 
col1 col2 col3 
col1 col2 col3 
col1 col2 col3    [7 rows of data in first "group"]
[COLOR=#0000ff]###[/COLOR]
data
col1 col2 col3 
col1 col2 col3 
col1 col2 col3 

etc...

Anyway, I used regex to replace '###' with just a line and that didn't change anything. I then tried to remove a line to see if it would catch in at least a few more lines of data, but nothing!

Also the refid.csv file is in Unicode UTF-8 format.

I'm not sure why it stopped after 8 rows but I need the rest in and I'm not sure how to force them in. I didn't have this problem at all with the other files I uploaded into different tables (and they had even more lines of data!).

**As a side note, if you were wondering why the first group has 7 rows but MySQL took in 8 rows, its b.c of one of the rows loaded into the table was:
```
[COLOR=#0000ff]##gff-version 3[/COLOR]
```

which is one of the three headers at the top of the file before the data rows (weird because it included that header but not the other two, then skipped to the first "group" of data rows (7 rows) )

---

### Post by jll339 on 2013-07-17
Thanks anyway but I finally figured it out. If anybody else is having similar problems then here is the solution:

I had four columns in my data and two of the columns were primary keys together for uniqueness, and while I had the correct primary keys (in that they are unique in my schema like they should be), I was actually putting the wrong data for one of those primary key columns. The data I DID put in incorrectly made it not unique, and that's why MySQL wouldn't put all my data rows in.
[U]
So if this happens to you[/U]: 
1.) rethink your primary key(s) schema in your table [B]
or [/B]
2.) make sure you are putting in the correct data in each column XP

---

