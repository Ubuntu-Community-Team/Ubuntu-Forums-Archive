---
title: "DB design and self referencing tables"
date: 2012-09-06
forum: Programming Talk
---

### Post by Kivech on 2012-09-06
Hi all,

I have a question about self referencing tables.

I'm a bit of an old rookie when it comes to programming and I date back from the days that Linux was only just available to the public. I was a programmer myself in those days, but mainly for mainframes and unix systems. 

I did my fair share of development and consequently also db design. For this I worked with environments like Oracle and AS400, but others as well.
In those days it was considered, at least in the environment in which I worked, to be a big 'no-no' to create self referencing tables. Performance was one of the main issues, but also problems with potentially creating an unmaintainable system.

In fact, one of the projects I did was to convert a system that was composed of only one table with all data in there, which was self referenced. After my conversion to a relational model, performance had improved drastically. For one search they did not have to go get coffee anymore, waiting for the results, but now they were instant.

My understanding is though, that these days, it has become more common to use self referencing tables. Due to my background I have developed the habit to avoid this practice at all times. Though I am curious to know why one would choose a self referencing table over a relational model with seperate tables using today's technologies.

So why would one choose to use a self referencing table over seperate tables with references?

I'm very curious to hear your opinion.

---

### Post by The Cog on 2012-09-06
I would think it depends on the type of thing that is being referenced. I can imagine for instance that a social club with a table of members (name, join_date etc) might also have columns for spouse or sponsor which reference other rows of the members table.

---

### Post by muteXe on 2012-09-06
In that case I'd have tbl_sponsor table, or something like that.
I haven't done DB design in a few years either, but i'd always prefer more tables over self-referencing ones.

---

### Post by Kivech on 2012-09-06
> **muteXe said:**
> In that case I'd have tbl_sponsor table, or something like that.
I haven't done DB design in a few years either, but i'd always prefer more tables over self-referencing ones.

Well, I have to agree with you, I would always prefer this approach as well. If only to keep data organized in a logical manner.

---

### Post by mevun on 2012-09-06
Not sure if I have a different concept of self-referencing table or not, so let me define mine.  A self-referencing table is one which has a column for referring to another row in the same table.

The obvious reason to use a self-referencing table (instead of multiple tables) is when the relationship can be "recursive" and/or infinite.  An example is parent-child where you might keep all family members and so to find a grand-parent, you would go back two references.  With "join tables" for this relationship, you'd need one of those for every level of relationship you want to track.  OTOH, if you're limited to searching for just parents and grandparents, then keeping those relationships in their own tables would speed that up.

Writing queries for self-referencing tables seems to require longer queries.  You probably have to give aliases for each "level" you're searching.  I don't know how performance suffers from this either.

---

### Post by JuhazOne on 2012-09-06
> **Kivech said:**
> So why would one choose to use a self referencing table over seperate tables with references?

Here's a story of what can happen with self-referencing tables.

I'm currently working on a project where we've tried this. We have a production database and a test database that have identical structure but the test database contains bogus data used in JUnit tests.

At some point we added the constraint that the column refers to another column in the same table. We then ran into a problem that the database mapper unit tests fail. Turns out the unit tests try to clean the table in the test database but this fails since internally the database doesn't drop all rows at once and you get failing constraints.

Quick search on the web didn't turn out any info on how to clear the referring column first and only then try to drop the rows. We ended up not using a constraint.

Later on we've come to the conclusion that we should have designed the database so that mostly there aren't these self-references. But this is for reasons other than ones related to database design.

---

### Post by The Cog on 2012-09-07
> **JuhazOne said:**
> Here's a story of what can happen with self-referencing tables.
That's a good reason not to use them.

Another reason: In the example I gave earlier, where a members table has a sponsor column referencing other members, this feels brittle or fragile to me. There is no way of having two sponsors for a member without adding a second-sponsor column. A separate table of (member, sponsor) would allow for any number of sponsors.

---

### Post by oldfred on 2012-09-07
The example I saw was a table for horses. It had the horse & its sire & dame.  Makes sense to only have one table of horses. 
The only issue I see is if someone types in the wrong name somewhere you could create an infinite loop, which would drive most queries crazy.

---

### Post by Vaphell on 2012-09-07
i think i've seen one such table at work during my very short database adventure. Its selfreferencing was used to record the history of changes (simple linked list)

```
|  id  | current |prev_id| (data)|
|------|---------|-------|-------|
|   666|    Y    |    333|       |
|   333|    N    |    222|       |
|   222|    N    |    111|       |
|   111|    N    |      0|       |

```

---

### Post by SeijiSensei on 2012-09-07
> **oldfred said:**
> The example I saw was a table for horses. It had the horse & its sire & dame.  Makes sense to only have one table of horses. 
The only issue I see is if someone types in the wrong name somewhere you could create an infinite loop, which would drive most queries crazy.

Even in this case I don't see a need to have self-referencing tables.  You can still have a single table of horses and two relational tables of sires and dames.  Each horse has a unique primary key, and the sires table would include records linking children to sires in the horses table, and another table linking children to dames.  Then you could still run a query like 

```
select horse from horses left join sires using (horse) left join dames using (horse) where sire='Secretariat' and dame='Ribbon';
```

This should return [Risen Star]("http://en.wikipedia.org/wiki/Risen_Star") and perhaps others, no?  I'm not a racing aficionado.  Or do I have my joins reversed?

---

### Post by trent.josephsen on 2012-09-07
In the horses example, sure, you *could* do it with three tables, but that is more complex than the self-referencing solution, requiring more validation (don't accidentally create a horse with two sires by fatfingering during table creation!) and more complicated SQL to get at the data you want.

That doesn't necessarily make it a *bad* or *wrong* solution. It's just more complicated. What you should be asking is, "Is this additional complexity *needed* or *helpful*?" Complexity may be necessary to future-proof your database or improve its performance, but if it's not, well, you could spend years adding complexity without gaining any measurable advantage. The question of whether or not to use a self-referencing table is a judgment call that ultimately falls on your head, and there's no hard-and-fast rule as far as I'm aware.

Disclaimer: I am not an expert on databases or decision-making.

---

### Post by SeijiSensei on 2012-09-07
> **trent.josephsen said:**
> In the horses example, sure, you *could* do it with three tables, but that is more complex than the self-referencing solution, requiring more validation (don't accidentally create a horse with two sires by fatfingering during table creation!) and more complicated SQL to get at the data you want.

Those kind of validation problems are handled by using "referential integrity" and well-defined primary keys.  Also most people use some type of front-end application to create the tables which can enforce rules like only-one-sire-per-horse.  I usually build applications with PHP front ends and PostgreSQL back ends.  I wouldn't let you create multiple sires.  I'd build forms to enter horses and let you specify parentage with [noparse]<select>[/noparse] drop-downs.

I'm also not sure the queries would be any more onerous.  Wouldn't you still have to use joins?

---

### Post by trent.josephsen on 2012-09-07
> **SeijiSensei said:**
> Those kind of validation problems are handled by using "referential integrity" and well-defined primary keys.  Also most people use some type of front-end application to create the tables which can enforce rules like only-one-sire-per-horse.  I usually build applications with PHP front ends and PostgreSQL back ends.  I wouldn't let you create multiple sires.  I'd build forms to enter horses and let you specify parentage with [noparse]<select>[/noparse] drop-downs.
Right. Primary key constraints and input validation on the front end are two aspects of the additional complexity I was talking about.

> I'm also not sure the queries would be any more onerous.  Wouldn't you still have to use joins?
I imagine it would depend on the features supported by the DB/DBMS as well as the exact nature of the query you were running. I'm not familiar with Postgres but I'm pretty sure you could trim it down to at most one join if you used a single self-referential table. In fact, you could do the equivalent with two sequential SELECTs... but it's been a few years since I did anything serious with SQL.

My point was, it is possible to think *too far* ahead, and it's the designer's responsibility to decide whether using three tables and two joins (where one table and 0-1 join will do) is necessary complexity, overengineering, or simply a waste of time.

---

