---
title: "Sqlite3, need help with creating a PHP database."
date: 2008-04-03
forum: Programming Talk
---

### Post by Gen2ly on 2008-04-03
hi guys, 

I need help creating a PHP database.  Because this computer is older I don't have resources to be able to install mysql so I was hoping to use sqlite3.  Unfortunately the documentation I'm reading only gives information for mysql but the php program does have support for sqlite3.  I need to create one database thats able to SELECT, INSERT, UPDATE, ALTER and CREATE a table.  It will also have three fields: username, hostname and database name.  Here's the mysql equivalent:

```
mysql -u database_user -h database_host -p database_name < dbstruct.sql
```

Anyone know how to do this with sqlite3?

---

### Post by smartbei on 2008-04-03
It is very similar:
```

sqlite3 database_filename < sql_filename

```
Keep in mind that in sqlite there is not notion of separate databases - each database is a file that you open with sqlite. To create a new database, just open a non-existent file.

EDIT: I am not sure what you mean by three fields - the command you gave for mysql did not use the username, hostname and database name as fields in the database or table. It used them to connect to the database server and select a database to work on. These 3 are not necessary with sqlite, becuase you are really just opening the database file.

---

### Post by Gen2ly on 2008-04-03
thanks for the information smartbei.  yes you are correct the line I gave is for importing a schema.  Unfortunately their is no documentation on how to create a database and I would appreciate help on creating one.  It looks like the program just needs a database file to use, so I'm looking on how to create a basic one.  

It looks like sqlite3 was able to create a basic database with no parameters once but (at least my version) is requiring some information before it will save (i.e doing "sqlite3 rss.db" then .quit will not save a file).  Any ideas?

Oh, the program i'm trying to install is [this one]("http://wiki.gregarius.net/index.php/Installation") if it helps.

---

### Post by stevescripts on 2008-04-03
> **Dirk.R.Gently said:**
> 
It looks like sqlite3 was able to create a basic database with no parameters once but (at least my version) is requiring some information before it will save (i.e doing "sqlite3 rss.db" then .quit will not save a file).  Any ideas?


A little help getting started with sqlite: [http://www.sqlite.org/sqlite.html](http://www.sqlite.org/sqlite.html)

Of course, your SQL could always be in a file.

Hope this helps a bit.

Steve

---

