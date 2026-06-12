---
title: "Problem importing csv file into mysql using load data infile"
date: 2012-04-26
forum: New to Ubuntu
---

### Post by Renjithrl on 2012-04-26
Hi,

   We are trying to import a simple CSV file into MySQL using LOAD DATA INFILE command.

MySQL Server Version : 5.0

Included below is the command and the response.

mysql> LOAD DATA INFILE 'MyData.csv' INTO TABLE MyDataBase.demographic (title, last_name, first_name);

Query OK, 5 rows affected, 12 warnings (0.06 sec)
Records: 5  Deleted: 0  Skipped: 0  Warnings: 12

The content of the csv file is :

"Mrs","Shri","Syama"
"Mr","Rob","Syama"

  Any idea whats happening wrong here..?
Do we need to specify the CSV or line separation here ..? 

Renjith

---

### Post by Vaphell on 2012-04-26
[http://dev.mysql.com/doc/refman/5.0/en/load-data.html](http://dev.mysql.com/doc/refman/5.0/en/load-data.html)

> LOAD DATA INFILE can be used to read files obtained from external sources. For example, many programs can export data in comma-separated values (CSV) format, such that lines have fields separated by commas and enclosed within double quotation marks, with an initial line of column names. If the lines in such a file are terminated by carriage return/newline pairs, the statement shown here illustrates the field- and line-handling options you would use to load the file:

LOAD DATA INFILE 'data.txt' INTO TABLE tbl_name
  FIELDS TERMINATED BY ',' ENCLOSED BY '"'
  LINES TERMINATED BY '\r\n'
  IGNORE 1 LINES;

If the input values are not necessarily enclosed within quotation marks, use OPTIONALLY before the ENCLOSED BY keywords. 

---

