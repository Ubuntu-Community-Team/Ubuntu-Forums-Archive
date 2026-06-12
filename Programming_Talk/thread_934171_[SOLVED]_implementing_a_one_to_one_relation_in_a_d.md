---
title: "[SOLVED] implementing a one to one relation in a database"
date: 2008-09-30
forum: Programming Talk
---

### Post by akudewan on 2008-09-30
Hi people,

I'm doing a college project (on Stock portfolio management) in which I need to develop a database.

I have 2 tables in the database (there are more, but considering 2 for the sake of brevity).

1) Stock (Stores details of stocks).
Fields are: StockID*, ValueOfPurchase, Quantity etc.

2) Bhavcopy (Stores an updated copy of current market values). Fields are: StockID*, OpenValue, CloseValue etc.

These 2 tables have a 1 to 1 relationship. The problem is, how do I implement it?

I think I can do one of the following:
1) Merge the two tables.
2) Use StockID as a Foreign Key in the second (Bhavcopy) table, along with a 'Unique' constraint
3) Keep the StockID as a Primary Key in both the tables
4) Make the StockID field a Primary as well as Foreign Key in the Bhavcopy table.

What is the best practice?
Any other suggestions?

Thanks

---

### Post by DrMega on 2008-09-30
Why would you implement a 1 to 1 relationship?

If the relationship is ALWAYS going to be 1 to 1, the logical thing would be to have all the applicable data in the same table. If you then wanted to restructed access to certain fields to certain users, I would create two views against the table, one with one set of columns and the other with the other set of columns.

That's the theory. In reality I would be more like to have one table (where the data is 1to1) and just run different SELECT queries against it depending on what I wanted back in a given scenario.

---

### Post by akudewan on 2008-09-30
Thanks for replying!

The thing is, I would have a total of 14 fields for the merged table.
And to add to the complication there's another table with a "zero-or-one to one" relation with the Stock table. (Its a table that stores all the stock IDs).

So should I go ahead and merge the three tables ?

---

### Post by DrMega on 2008-09-30
> **akudewan said:**
> Thanks for replying!

The thing is, I would have a total of 14 fields for the merged table.
And to add to the complication there's another table with a "zero-or-one to one" relation with the Stock table. (Its a table that stores all the stock IDs).

So should I go ahead and merge the three tables ?

Where there is ALWAYS a 1 to 1 relationship, they should all be in the same table. The number of columns is only an issue if it breaches the technical limitations of the database engine. For example, some very old database engines had a limit of 16 columns per table. This isn't an issue with modern implementations which often allow more columns than you'd usually need for one table.

Where there is a relationship which can be anything other than 1 to 1 (eg 1 to 0 or many), you should use a seperate table.

Consider the following requirement. If I have to store a list of customers names and account numbers, and I also have to store there home address, I would store all this data in one table. If SOME but NOT ALL of the customers own a car, and I need to store their car details, I would have a seperate table for customers cars, with a foreign key index associated with the customer primary key. The customer may own no car, in which case there would be no record in the cars table. They may own 1 car, in which case the relationship would be 1 to 1, but we can't assume that because they may own two or three cars.

In a customer database, we will also likely have an customer order table. This would be seperate again because it has nothing to do with their car ownership, and a customer may have ordered once, or many times.

So, to reiterate and sum up, where the relationship is ALWAYS exactly 1 to 1, put them in the same table. Any relationship other than that means we need seperate tables.

Just one last point. If the relationship could be EITHER 1 to 1 or 1 to 0, still use a seperate table if the row that might not exist has more than one column, otherwise you have to live with loads of nulls in your result set.

In practice, all of this means you'll need to ensure you are brushed up with two key aspects of DB development. Make sure you know all about keys and indexes, and also make sure you've brushed up on all your joins (INNER, LEFT OUTER, RIGHT OUTER and FULL OUTER), otherwise you'll get some funny results from your queries.

Good luck, and any more questions, just post them up.

EDIT: There is one exception to the rule of putting all 1 to 1's in the same table. If the two sets of data are nothing to do with each other, then go ahead and use two tables. For example, you might coincidently get a 1 to 1 between customer and retail outlet (not in practice of course - just in theory) but you wouldn't lump them together because there is always the possibility that a retail outlet might close or a new one opens or a customer suddenly chooses a different retail outlet). Sorry for the bad example but I couldn't think of a more realistic example just at the moment.

---

### Post by akudewan on 2008-09-30
Thanks for clearing it up!

One more thing though, as for the "zero-or-one to one" relation, I'd have to make 2 separate tables, or I'd have most of the values as null, as you mentioned. So how should I implement this relation? Using a Foreign Key, or any of the methods I've descibed in the first post?

---

### Post by DrMega on 2008-10-01
> **akudewan said:**
> Thanks for clearing it up!

One more thing though, as for the "zero-or-one to one" relation, I'd have to make 2 separate tables, or I'd have most of the values as null, as you mentioned. So how should I implement this relation? Using a Foreign Key, or any of the methods I've descibed in the first post?

Your table that might not have a row (ie the '0' end of the zero or one to one) would have a foreign key field which would link to the primary key on the 'one' end.

I would then just have a view that joins the two tables using a LEFT OUTER join, something like this (syntax is MS SQL, not sure of equivalent MySQL):

```

CREATE VIEW view_BothTablesJoined AS

SELECT a.fld1, a.fld2, a.fld3, b.fld1, b.fld2, b.fld3
  FROM TableWhichAlwaysHasARow a
  LEFT JOIN TableWhichSometimesHasARow b
  ON b.ForeignKeyField = a.PrimaryKeyField


```

Obviously you'd choose meaningful names for the tables and fields, but that's the basic principle of it.

Two things to note. Firstly, always list the fields individually rather than using '*' to get them all. This is partly for readability and partly because some DB engines (MS SQL for example) throw a wobbler if a view uses '*' to get all fields and then you later change the structure of any of the source tables.

The second thing is I never create the relationships directly in the database schema except by using views. In my experience it is far less complicated to maintain referential integrity if you do so in your own code. It just means that it is always clear what's going on. The trick is to develop stored procedures for all the common actions, that way you get to choose all about what validation etc you want to implement. The use of triggers is also a great way to ensure that everything does exactly what you've told it to do.

---

### Post by tec.kishroe on 2008-12-04
Hi,

I stuck up on how to implement a one-to-one or many relation.

Requirement is User has one compulsory(primary) address and many optional(secondary) addresses..

My design is User Table and Address Table with foreign key in Address table pointing to User Table primary key....but I'm missing the constraint that there should exist one address....any idea how to implement in physical database....

Thanks....

---

### Post by howlingmadhowie on 2008-12-04
The obvious solution would be to add fields for one address in the user table and then set the column definitions to be not null. then in your second table you store optional addresses over the userid

---

### Post by tec.kishroe on 2008-12-04
thanks for the quick response...is it the only to implement one-to-one or many relationship. there will be some problems in implementing the same in hibernate......

---

### Post by howlingmadhowie on 2008-12-04
if you're using hibernate, aren't there some annotations in your java code which could help you?

---

### Post by tec.kishroe on 2008-12-04
there is a way to implement this in hibernate...but i would like know how it one-to-one or many relation is handled in general......

---

### Post by pp. on 2008-12-04
> **tec.kishroe said:**
> I stuck up on how to implement a one-to-one or many relation.

Requirement is User has one compulsory(primary) address and many optional(secondary) addresses..

Actually, these are two relations which are somwhat 'related'.

Relation one is from address to user. Each address pertains to one and only one user, each user can have any number of addresses. Typical one-to-many case.

Relation two is from user to address. Each user must have one and only one "main" address. Making the foreign key in user (referring to address) mandatory will partly fulfill your requirement. If the primary key of address is (user, address#), the job is done. If the primary key of address is (address#) only, you'd have to add an additional constraint in order to make sure that the main address for each user actually belongs to that user.

---

### Post by tec.kishroe on 2008-12-05
thanks for your input....
in that case your are ending up with foreign keys(not null) in both tables, which will be problem while inserting data. Your user id is required to add data to address table and address id is required to add data to user table......any suggestions....

> **pp. said:**
> Actually, these are two relations which are somwhat 'related'.

Relation one is from address to user. Each address pertains to one and only one user, each user can have any number of addresses. Typical one-to-many case.

Relation two is from user to address. Each user must have one and only one "main" address. Making the foreign key in user (referring to address) mandatory will partly fulfill your requirement. If the primary key of address is (user, address#), the job is done. If the primary key of address is (address#) only, you'd have to add an additional constraint in order to make sure that the main address for each user actually belongs to that user.

---

### Post by pp. on 2008-12-05
> **tec.kishroe said:**
> thanks for your input....
in that case your are ending up with foreign keys(not null) in both tables, which will be problem while inserting data. Your user id is required to add data to address table and address id is required to add data to user table......any suggestions....

Can't you insert into a view?

---

