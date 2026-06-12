---
title: "how do you insert a lot of rows into MySQL?"
date: 2015-05-14
forum: Programming Talk
---

### Post by stupidquestion on 2015-05-14
I'm using PHP to insert random data into MySQL for testing, but this crashes the page if there are too many rows. How do you insert an unlimited number of rows into MySQL?

By the way I just inserting one row at a time. I'm also doing a select before each insertion because each random row has to be one of the values specified by the database.

---

### Post by SeijiSensei on 2015-05-14
1) Set up an ODBC or JDBC connection to the database and upload data from a spreadsheet.

2) Using the method you described, are you running PHP in Apache, or from the command line?  If the former, I suggest running the script from the command prompt to avoid the page length issue you describe.

I'm a PostgreSQL user.  I usually upload data by first writing a tab-delimited file then reading it with PostgreSQL's COPY command.  A quick search of the MySQL documentation didn't immediately bring up a parallel method, but I bet there is one.

---

### Post by Habitual on 2015-05-15
> **SeijiSensei said:**
> A quick search of the MySQL documentation didn't immediately bring up a parallel method, but I bet there is one. And you would be correct, [INFILE]("https://dev.mysql.com/doc/refman/5.1/en/load-data.html")
If straight mysql "insert into" statements, then ```
mysql -uroot -p <db> < /path/to/input/file.sql
```
I think it depends on how the bulk data is formatted in the source file, yes?

Other methods may be presented also...

---

### Post by stupidquestion on 2015-05-16
> **SeijiSensei said:**
> 1) Set up an ODBC or JDBC connection to the database and upload data from a spreadsheet.

2) Using the method you described, are you running PHP in Apache, or from the command line?  If the former, I suggest running the script from the command prompt to avoid the page length issue you describe.

I'm a PostgreSQL user.  I usually upload data by first writing a tab-delimited file then reading it with PostgreSQL's COPY command.  A quick search of the MySQL documentation didn't immediately bring up a parallel method, but I bet there is one.

Thanks, I've tried these methods. Running from the command prompt seems to be the easiest way since so far it hasn't timed out.

---

