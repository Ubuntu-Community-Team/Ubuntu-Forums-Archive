---
title: "SQL Questions - Index question and trigger/stored proc question (MySQL)"
date: 2008-06-20
forum: Programming Talk
---

### Post by evymetal on 2008-06-20
General question about mysql, it's very important this runs as fast as possible. I'm fine with general suggestions, but when Replying please state how confident you are in your answer.

Suppose I have this schema (ignoring indexes for now)
****

```

-- pk# are all primary keys
-- fk# is a foreign key on pk#
-- mappingstable will have lots of entries for each row in table1

CREATE TABLE table1 (
    pk1 SERIAL,
    property1 INT
    )
;

CREATE TABLE table2 (
    pk2 SERIAL,
    fk1 INT,
    property2 INT
    )
;

CREATE TABLE mappingstable (
    fk1 INT,
    property3 INT,
    num FLOAT
)
;

```

And now I want to do this select (this is massively over simplified, but shows the point of the question):

```

SELECT
    SUM(mappingstable.num)
FROM
    table1
INNER JOIN
    table2
ON 
    table2.fk1 = table1.pk1
INNER JOIN
    mappingstable
ON
    mappingstable.fk1 = table1.pk1
WHERE
    mappingstable.property3 in (1,4,2,6)
    AND
    table1.property1 = 2
    AND
    table2.property2 = 3
GROUP BY 
    table1.pk1

```

Questions:

 * EXPLAIN ... shows one STANDARD select that is being performed using ANY - I assume that's the SUM(), and that the WHERE actually means that it's not running on every row (or at least I hope so!) - it's the first row in EXPLAIN...

 * Indexes: obviously there are indexes on:
table1.pk1
mappingstable.fk1

.. but should the index on mappingstable.property3 be on
mappingstable.property3
or on
(mappingstable.fk1,mappingstable.property3)

(and so on for the other properties in the WHERE clause)

.. thinking about it, it instincively seems best to have these indexes:

mappingstable.property3
(table1.pk1,table1.property1)
(table2.fk1,table2.property2)

.. But am I right?



**Second Question**

I have a table that has to be dealt with very carefully to keep temporal information in the database, i.e. rather than performing a standard UPDATE, I create a new row with the same id (a virtual primary key) and the new information, and set a flag on the old row to an "old" status.

The problem is that developers who may not have a really in-depth knowledge of SQL (or this schema) may be accessing this database, so I want to make this as invisible as possible. (other table have to be updated with references to this new row too)

My options seem to be 
 * To create a set of stored procedures and only grant access to this table through these
 * To Create a "dummy" table that developers are free to access / update as much as they want, and add loads of triggers to them.

I've never used triggers, but it seems that may be the better option as developers would just see it as a normal table - has anyone got any experience or advice on what to use?

---

### Post by brentoboy on 2008-11-18
create *_old tables

don't mark a record as inactive.

keeping historical changes is often important to the integrity of a database, so I agree that you shouldn't just delete old data, or update old rows without a history to track, but you'll get all kinds of issues with your relationships that you dont really want if you have multiple records that have the same ID, it will also further complicate your table joins as you will have to add additional logic to keep the active record straight, and it wont be as easy to understand for new devs.

Also, when you do table sorts and merges, you will have tons of irrelevant records what will have to be sifted, sorted, and dropped from result sets.  Doing a SQL join creates a (temporary) cross product of all the records in all the tables.  doubling the size of all the tables when it isn't even real data is going to make your queries run slower.

oh, and do it on a trigger, lie you said, becuase you don't want newbie developers to update your records without knowing they were supposed to move the old version into the _old table.

That's my advise.

---

### Post by drubin on 2008-11-18
> **brentoboy said:**
> 
Also, when you do table sorts and merges, you will have tons of irrelevant records what will have to be sifted, sorted, and dropped from result sets.  Doing a SQL join creates a (temporary) cross product of all the records in all the tables.  doubling the size of all the tables when it isn't even real data is going to make your queries run slower.

Proper indexes. (on the joining rows) can hugely decress the number of records looked at.

What types of numbers are you referring to?
Amounts of joins.
Number of records in each table.

With the proper indexes on tables/records and with a good design mysql handles HUGE amounts of data quite happily.

---

