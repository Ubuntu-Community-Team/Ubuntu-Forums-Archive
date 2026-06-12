---
title: "import data in MySQL from file"
date: 2008-03-11
forum: Programming Talk
---

### Post by Krijk on 2008-03-11
I've created input files that I want to import in MySQL using a bash-script. I'm not sure how to start within the MySQL shell. Basically I want to do the following:

**Format import file **
```
data1field1;data1field2;data1field3;data1field4
data2field1;data2field2;data2field3;data2field4
```

In order to achieve this in mysql I have to do the following:

**Option 1**
```
mysql -u import -p password
mysql>use database_to_import_in;
mysql>INSERT INTO table
(field1, field2, field3, field4)
values
(data1field1, data1field2, data1field3,data1field4);

```
[B]
Option 2[/B]
```
mysql -u import -p password
mysql>use database_to_import_in;
mysql>LOAD DATA LOCAL INFILE '/importfile.txt'
INTO TABLE table
FIELDS TERMINATED BY ';'
LINES TERMINATED BY '\n'
(field1, filed2, field3,field4);
```

What is the most flexible way to do this. For example if I want to do a check on the database such as update if record already exists or append if the record is new. 
Option 1 is probably better for this, but I'm not sure how to put this in a bash-script. Especially with a loop so the inputfile is read line by line.

---

### Post by pmasiar on 2008-03-11
LOAD DATA is preferred for bulk load, because INSERT rebuilds indexes after every insert. INSERTing lot of data can take quite long time (you may averate, depending on disk speed, DB structure and complexity of indexes, only couple, or up to dozen records INSERed per second). YMMV, test before you leap. INSERT is OK if you need to put in just couple rows.

---

