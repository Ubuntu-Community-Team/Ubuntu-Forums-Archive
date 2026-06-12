---
title: "Table name as i/p to Stored Procedure"
date: 2007-05-21
forum: Programming Talk
---

### Post by derby007 on 2007-05-21
Can I pass a Table name as a variable into a stored procedure, that would then do an SQL statement : SELECT * from 'table_name';
ie. it would populate a ResultSet based on the Table name going in?

---

### Post by rfreedman on 2007-05-21
The general answer is no. 

More specifically, it depends on which database you are using.

While most database stored procedure languages would not allow the table name to be a variable, some have ways around this. 

For example, Oracle has "execute immediate", which allows you to execute a sql statement stored in a string.
So in a proc in Oracle PL/SQL you could do something like:

    str_sql := 'select * from ' || tablename;
    execute immediate(str_sql);

---

