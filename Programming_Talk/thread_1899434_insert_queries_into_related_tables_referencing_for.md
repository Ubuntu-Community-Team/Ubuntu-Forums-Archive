---
title: "insert queries into related tables referencing foreign keys using python"
date: 2011-12-23
forum: Programming Talk
---

### Post by memilanuk on 2011-12-23
So... most python-sqlite tutorials concentrate on single tables.  The few that deal with multiple tables and that mention foreign keys and such seem to demonstrate mainly using hard-coded data instead of parameterized insert queries into tables with auto-increment primary keys.  For the most part I'm able to figure things out as I go using a variety of documents both print and electronic... but when I don't *know* the pk number (because its automatically assigned) it makes it tough to supply it as a foreign key for another insert query into related tables.

Whats the 'right' way to do this sort of record insert or update query?  Insert into the main table first, then do a select query to find the last rowid and store it in a python variable and then use that as a parameter for the rest of the insert queries to related tables?  Or is this something an ORM like SQLalchemy would smooth over for me?

---

### Post by r-senior on 2011-12-24
An ORM will undoubtedly handle it but you don't need an ORM to achieve the same result. The difficultly is that primary key generation is not standardised and is database-specific.

If you take the Oracle database as a example, it typically uses sequences to generate primary keys. A sequence is a database object that returns unique values on request. When creating a master/detail relationship, a new primary key value is obtained from a sequence and used to populate the primary key column on the master. This is then assigned to the foreign key columns on the detail records.

MySQL takes a different approach. The primary key column on the master is generally set to auto-generate and the primary key obtained from the master record after insert (but before commit) using the last_insert_id() function. This value is then assigned to the foreign key columns as above.

So in your Python code, I would say you need to do exactly as you suggest. Just bear in mind that the database probably provides a mechanism to get the generated primary key other than by querying back the record you just created.

The other consideration, of course, is that the various inserts need to be wrapped in a transaction so that either the whole set commits or the whole set is rolled-back on error. Exception handling becomes important.

The Data Access Object (DAO) design pattern, although often associated with Java, is equally applicable to other languages, and is well worth considering to encapsulate this database specific away from your program.

EDIT: You didn't mention a database in your post but I noticed you tagged it SQLite. If you have an INTEGER PRIMARY KEY column, it will automatically be populated if you don't specify a value on insert. You can then use the ROWID column to get the assigned row identifier for a record you inserted. Same idea as last_insert_id() with MySQL.

---

### Post by memilanuk on 2011-12-24
Question for you on the lastrowid for sqlite (or similar feature for mysql)... does it just get the lastrowid that has been inserted by the cursor object you currently have open... what happens if some other process inserts a row in the interim?  Would you get 'your' lastrowid, or 'their' lastrowid?

TIA,

Monte

---

### Post by r-senior on 2011-12-26
[http://www.sqlite.org/c3ref/last_insert_rowid.html](http://www.sqlite.org/c3ref/last_insert_rowid.html)

Note the last paragraph and the words "same database connection". They key to avoiding the problem is to use "thread confinement", i.e. not to share connections between threads.

---

