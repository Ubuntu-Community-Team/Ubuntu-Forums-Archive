---
title: "Better PHP MySQL integration (?)"
date: 2007-02-15
forum: Programming Talk
---

### Post by Note360 on 2007-02-15
Any way I have been working on a easy to use php wrapper for MySQL. It wont replace simple mysql_query(), but it could make things easier. So far I have very little, but here is what I have.

```

table1 = new Table;
table1 = table1->setTableInfo( 'joe' );
table1->newColumn( 'column_name', 'column_type' );

```

It is very basic currently and requires the table to be already created. However I am working on it. I am not sure how to handle creating tables.

Also if their is also a project like this inform me. Is this wanted? (I am still working on it i'll get it out soon, cause I have a snowday today)

---

### Post by kidders on 2007-02-15
Hi there,

I would never use something like this, but it _does_ sound sensible & worthwhile. If it doesn't exist already, it definitely should!

> **Note360 said:**
> I am not sure how to handle creating tables.I'm not completely sure what you mean by this, but perhaps it has something to do with the idea that creating a table before there are any fields in it would be ... well ... strange. May I suggest one small change:

```
$table1 = new Table**('tablename', false)**;
$table1 = table1->setTableInfo( 'joe' );
$table1->newColumn( 'column_name', 'column_type' );
```

I wonder if something like this would work:
[LIST]
[*]The second argument I tagged onto your **Table** constructor would be an optional (default=false) boolean called something like **allow_create**.
[*]**$table1** would be set to false if **allow_create** were false (or unspecified) and a table by the specified name didn't already exist.
[*]No "CREATE TABLE..." SQL would be executed by the constructor at all.
[*]"new"-ing a **Table** object would be used both to acquire a reference to an existing table, and to create new ones.
[/LIST]

You could then create a function called something like **Table->commit_changes**, which would perform any pending SQL operations on a table. That way, you could put off actually creating a table in SQL for as long as possible. Certain functions in your **Table** object would call **commit_changes** implicitly, or a user with advanced knowledge could do so explicitly, much as users currently have the option of calling SQL functions like **free_result** themselves.

Imagine this...

```
$table1 = new Table**('tablename', true)**;
$table1 = table1->setTableInfo( 'joe' );
$table1->newColumn( 'column_name', 'column_type' );
$table1->newColumn( 'column_name', 'column_type' );
...
...
...
$table1->newColumn( 'column_name', 'column_type' );
$table1->insertRow(array('column_name'=>'value'...));  **<- CREATE occurs here**
```

Imagine "insertRow..." is line 100 of a long list of operations.
[LIST]
[*]If an error occurs on line 75, no table will exist that would now have to be cleaned up.
[*]If no error occurs, one single SQL query would replace what looks like 100 separate queries, to create the table.
[*]If the table "tablename" already existed, the SQL being held back would be an "ALTER TABLE..." rather than a "CREATE TABLE...". In this case, users would be glad to read a note in your API to the effect that alterations that *appear* to be performed in stages are in fact atomic (ie a table creation/alteration could never be only partially completed due to a runtime error).
[/LIST]

You might find these completely dumb suggestions! Your thread interested me though, so I thought I'd at least have a go. :-)

---

### Post by Note360 on 2007-02-15
this all makes perfect sense. I am gonna need help let me get a prototype with the basic features out soon.

creating tables
creating columns
inserting data
displaying data w/ some where ability (obviously pretty hard to do)

When I get that I will post it.
I am going to make a google code page eventually.

---

### Post by Mirrorball on 2007-02-15
There are several projects like this already. Have a look at AdoDB, Propel, PHP Doctrine, the database component in the Zend Framework etc.

---

### Post by Note360 on 2007-02-15
> **Mirrorball said:**
> There are several projects like this already. Have a look at AdoDB, Propel, PHP Doctrine, the database component in the Zend Framework etc.

Ok, well then Ill continue with mine jsut for the sake of learning for a bit. Ill look into these ones. I don't think I'll be able to beat any of these.

---

### Post by kidders on 2007-02-15
> **Note360 said:**
> Ok, well then Ill continue with mine jsut for the sake of learning for a bit. Ill look into these ones. I don't think I'll be able to beat any of these.

There *must* be some new angle you could explore. I'm not familiar with any of the projects Mirrorball mentioned (so these ideas may also be well covered), but perhaps you could find some way of making some quirky SQL tasks easier, or allowing users of your "Table" class to type **table->setEngine('postgresql');** or **table->setEngine('oracle');**. Perhaps you could explore ways of having your project automatically handle some of the relational constraints missing from MyISAM tables.

Basically, I can't help wondering if there is some way you could trump existing MySQL wrappers by:

[LIST]
[*]Adding new behaviour to MySQL for people who don't want to use, say, InnoDB.
[*]Bridging the gap between MySQL 4 and MySQL 5, so people can port code more easily.
[*]Allowing people to write PHP code that is completely independent of any database engine.
[*]Finding a neat way to trade flexibility for brevity in peoples' PHP code.
[/LIST]

Also, although MySQL is already able to churn out usage stats (so you can evaluate the efficiency of your code), having some equivalent of that, written in PHP, that was able to give you much more detailed information, might be useful. How about a "Table" class that monitored how it was being used, while it chatted with the database?

---

### Post by Note360 on 2007-02-15
Ok, I am trying to debig the code now and I'll get a super inept version up soon

---

