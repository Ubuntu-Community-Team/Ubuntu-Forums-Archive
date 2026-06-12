---
title: "DBMS and RDBMS shortcomings and errors"
date: 2024-01-28
forum: Programming Talk
---

### Post by ronakmehta on 2024-01-28
I hope you're well. I'm now immersed in the intriguing world of Database Management Systems (DBMS) and Relational Database Management Systems (RDBMS), but I've found a few roadblocks along the way. I'm contacting you to ask your assistance in overcoming these challenges.


Here's a sample of the SQL code I've been working with:

```
-- Creating a table in an RDBMS
CREATE TABLE Employee
    EmployeeID INT PRIMARY KEY,
    FirstName VARCHAR(50),
    LastName VARCHAR(50),
    Department VARCHAR(50);



```

In this SQL code sample, I've highlighted four issues that I'm working on:


1.The CREATE TABLE statement looks to have a syntax issue. Can you help me find and rectify the syntax mistake that prevented me from correctly creating the "Employee" table?
2.While attempting to specify the primary key for the "Employee" table, I received an error message stating "missing '(' after 'PRIMARY'". How can I fix this problem and correctly declare the main key?
3.The data types for the columns "FirstName," "LastName," and "Department" are provided, but I am not sure whether they are suitable. Could you please advise on picking acceptable data types for these columns?
4.I added semicolons at the end of each line, but I'm not sure if this is essential or if it would cause problems. As shown in that [publication]("https://www.scaler.com/topics/difference-between-dbms-and-rdbms/"). Should semicolons be used in this situation, and if not, what is the proper approach?


Your advice and knowledge would be highly appreciated as I navigate these obstacles. Thank you for your time and support.

---

### Post by TheFu on 2024-01-29
There are different flavors of SQL, so you'll need to start by picking a specific SQL Server.
Most SQL requires a **commit;** statement to actually do anything, unless you enable autocommit, which is a bad practice, especially for a DBA.

I see the issue.  It seems you think the indentation matters and it is hiding some missing ().

This might help:   [=detailed&q=What%27s+wrong+with+this+SQL%3F+CREATE+TABLE+Employee%0A++++EmployeeID+INT+PRIMARY+KEY%2C%0A++++FirstName+VARCHAR%2850%29%2C%0A++++LastName+VARCHAR%2850%29%2C%0A++++Department+VARCHAR%2850%29%3B"]https://iask.ai/?mode=question&options[detail_level]=detailed&q=What%27s+wrong+with+this+SQL%3F+CREATE+TABLE+Employee%0A++++EmployeeID+INT+PRIMARY+KEY%2C%0A++++FirstName+VARCHAR%2850%29%2C%0A++++LastName+VARCHAR%2850%29%2C%0A++++Department+VARCHAR%2850%29%3B]("https://iask.ai/?mode=question&options[detail_level)

And you'll have another method to find mistakes without waiting.

---

### Post by SeijiSensei on 2024-01-29
I use PostgreSQL. The CREATE TABLE command requires parentheses like this
```
CREATE TABLE tablename (col1 type1, col2 type2, etc.);
```

SQL is pretty picky about syntax. PG will bring up a documentation page if you type:
```
\h create table
```
returns
```

Command:     CREATE TABLE
Description: define a new table
Syntax:
CREATE [ [ GLOBAL | LOCAL ] { TEMPORARY | TEMP } | UNLOGGED ] TABLE [ IF NOT EXISTS ] table_name ( [
  { column_name data_type [ COMPRESSION compression_method ] [ COLLATE collation ] [ column_constraint [ ... ] ]
    | table_constraint
    | LIKE source_table [ like_option ... ] }
    [, ... ]
] )
etc.

```
I don't use MySQL unless I have to, but I think the commands for documentation are different there.

---

### Post by ronakmehta on 2024-02-29
Thank you so much for help you both

---

