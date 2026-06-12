---
title: "Create a subquery that has a &lt;create view&gt;"
date: 2009-02-19
forum: Programming Talk
---

### Post by theDaveTheRave on 2009-02-19
Hello all

I don't know if this is possible or not but as the title suggests I am wondering if it is?

the scenario.

I have 2 tables of data, with an equal primary key

table1 = contains 17  rows (lets call them 1 - 17)

table2 = contains rows (lets call them 'a', 'b' and 'c')


I have a list of query values that will be equivalent to the info found in rowb of table 2.

I would like to obtain the values from rows 'a' and 'b' from table 2, and include the value of row 2 from table 1.

the return values of row 'a' from table 2 will give me the required detail from table1.row2

so my 2 search queries are:

```

select rowa, rowb from table2;

```

which does exactly what I would expect.

Now I have tried to select across from the first table with the following...
```

select row1, row2, rowb from table1, table2
where table2.rowb in(val1, val2....)

```

as the table columns are in fact called the same I am using fully qualified column names in all instances.

but it crashes my pc?

The 2 tables contain 4909607 and  10325282   respectively, could this be my issue? - I've just realised how big table2 is :p

I have tried to create a work around, by creating a view of table2 containing just the 17 values that I want to search, and then use this view as the <IN> part of my where clause, but I get the same thing.

Or is there another way to work around the problem?

I can quite happily do either select on it's own merrit, but it is a pain having to cut and paste the results of the first search so as to then grab the required results from the second, then I have to join them up again manually...

and I have tried to create 2 views and <join> them, but this seems to have the same effect!

Should I really create 2 bona fide tables? is this going to be my best solution, then simply "drop" the tables once they are no longer required?

Are there any other solution that may spring to mind?

I am using INNODB tables, if this makes any difference!

this isn't really a HUGE problem, just interesting (I think).

And in case you are interested I have genetic / protein data in my tables.

Thanks for your help and suggestions in advance.

David.

ps, the MySQL server is running on a dual core athlon with 2GB memory... I still need to convince my boss to allow me to use the quad core server (that has 8gb memory), that is currently acting as a "file share". Would it be worth my while trying to convince him that I should have the data tables there in stead!?

David

---

### Post by kidders on 2009-02-20
Hi there,

> **theDaveTheRave said:**
> I have 2 tables of data, with an equal primary keyOut of curiosity, why is the data split across two tables, if the primary keys are equal?

Unfortunately, running "SELECT ... FROM table1, table2" with a WHERE clause that only references table2 will generate an intermediate recordset with approximately 50.7 trillion rows in it, each of which has to be scanned to see if it satisfies your IN condition. Imo, that's waaaay out of MySQL's league. What kind of comparison & indexing is involved would be worth posting, but tbh, I'm not sure trying to make the query more efficient would make it any more likely to succeed. :-(

I can't claim to be very experienced in dealing with these kinds of volumes of data, but there is no way a default MySQL install would handle your query. It *might* be possible to tune it enough to persuade it not to crash, but I can't help wondering if a different platform would be worth exploring. Do you suppose PostgreSQL or Oracle would do a better job?

> **theDaveTheRave said:**
> Would it be worth my while trying to convince him that I should have the data tables there in stead!?I'd have to read up on how far MySQL can be pushed to answer that question with any authority. The answer also depends very much on your data & the nature of the comparisons necessary to perform your query. For example, the worst case scenario would obviously be 50 trillion full table scans, comparing unindexed (or unindex*able*) text ... I doubt a better computer would make the slightest difference!

Anyhow, I hope that helps.

---

### Post by theDaveTheRave on 2009-02-20
Kidders

thanks for the response, it made me smile when I realised that I could be creating an intermediate table with 50.7 million datapoints...


```
Out of curiosity, why is the data split across two tables, if the primary keys are equal?
```

The data sets contain almost entirely different information. One is linking to various other indexing values.

for instance, each gene is given an ID (lets say G1), it can relate to a Protein (p1) by way of an intermediary messenger (m1)

However.

the same gene (g1) can also have an official "name" (or "symbol), let say it is n1.

Now here is where it becomes interesting... Each gene can be represented in different organisms (humans, mice , politicians etc). So now our gene official name "n1" has an id of g1 in humans, g2 in mice, and g3 in all lower life forms (or politicians).
BUT each of these (g1, g2 and g3) give rise to the same protein (p1).

Now we get complicated...

Protein can has "isoforms" - think of it like a car, same model, but different colour. So now p1-bule, is the same (for its activity/function etc) as p1-red.

The tables I am working with are like this....

table 1 contains all the gene construcs and messenger stuff.
table 2 conains the info on the organism etc.

Ready for the horrible part...

each gene (g1) can give rise to more than one messenger!

so each table gets progressively larger, hence I split them into species data. and then I concentrate those down to just the stuff that my team is interested in.

I do in fact run this sort of query accross my tables all the time, admitedly it can take a while!

for example, I have a table that contains all the info for the geneID and relates it to the messenger and protein values.

I will use this list as part of my where clause to create another table.

eg
```


select * from lotsOfGeneInfoTable
where geneID in (
Select teamTable.GeneID from teamTable);


```

which works a treat,

I've got scripts to create whole loads of data from different places.

It pulls out info, and then creates new tables to join to that information.

I guess that the way I did the query in the end - by creating a table out of my inner select, then use the primary key in this now much smaller table of only 50 entries (out of the 4 million or so that are in the table).

I then crossed this new table with the table in the outer. both sets of queries got the data that I wanted in about 3 minutes (total)

One thing I will say, the flat files take about 15 to load into mysql.... thank god for the coffee machine!

If I though I was going to be doing this a lot I guess I would write an proper script for it. But it was just my boss wanting to check the data that he had had, and not wanting to send each of the 50 to the web page one at a time... so much quicker really.

David.

---

### Post by kidders on 2009-02-20
Ahh... That makes much more sense ... The relational model is clearly fine. The "equal primary keys" bit threw me, when in actual fact, you were talking about foreign keys. Sorry.

Depending on how good you are with SQL (and MySQL), none of this will necessarily be of any help, but there's one way to be sure ...

**I - Denormalising data**
Say I wanted to group photos together into lists. The "correct" model would involve three tables ...

**PhotoGroup**: _id_, title
**Photo**: _id_, label, filename
**PhotoGroupMembership**: _id_, photo_id, photogroup_id, display_order

Pretty much no matter what question you want to answer (eg "what groups is photo x in", "what photos are in group y"), getting it involves at least one join. Deliberately mis-modeling the data eliminates that problem ...

**PhotoGroup**: _id_, title, photo_ids
**Photo**: _id_, label, filename

... where "photo_ids" is a comma-delimited list of foreign keys.

Anyhow, I can't help wondering if your data could be structured that way, given the constraints doing so would impose. The goal would be to get the maximum possible amount of information out of a single "SELECT * FROM table WHERE id=x" query.

I once wrote an application that did this sort of thing. The denormalised version of the data acted as a sort of cache for the strict relational model, eliminating the need for complex joins, just to find the answers to simple questions. I recomputed the cache every now and then, to keep it fresh.

**II - Tuning MySQL**
phpMyAdmin contains a useful tool for spotting badly designed queries, mis-tuned database engines, badly optimised tables, etc. As a simple example, memory-based temporary tables are (obviously) more efficient than disk-based ones. Allocating more RAM for use as temporary tables could cut down on the amount of disk-thrashing involved in a big join. Unfortunately, that particular example probably won't get _you_ anywhere ... your tables are just too big.

**III - Indexing**
What kind of indexing are you using? It occurs to me that in extreme cases, queries can actually perform better without it. The only *remotely* comparable example I have practical experience of is with things like IP-to-location databases. Typically, they consist of a gigantic table with a compound primary key, representing a numeric range within which an address must fall to be in a particular region. Aware that executing "SELECT * FROM table WHERE address BETWEEN a AND b" essentially requires a full table scan every time, you might be tempted to create an index on "a" and "b" (the compound key). In practice however, "a" and "b" are so wide that the index can wind up being multiples of the size of the table itself!

Anyhow, I half expect (a) that you know all this already, or (b) that there is no way to apply any of it to your particular database, but I thought I'd give it a whirl.

Interesting problem though ... and interesting subject matter!

---

### Post by theDaveTheRave on 2009-02-20
kiders

glad you like my problems!!!

when it comes to normalising (or not) the data base tables I have some real problems.

Most are created due to the insane size of the data sets. I know for instance that each of the gene / protein types get given classes / functionality groupings, etc.

But thinking about creating lots of tables, probably somewhere like 7 or 8, each with umpteen million records that will map a geneID to a given funcional group etc etc...not only does it make my head hurt thinking about how I would be best to go about this, but I'm not sure it would make any real performance difference. Particularly because we are interested in searching only for the primary keys in the various tables., the exta data is often just that... extra, often interesting but you need to see it as you have no idea if it is interesting untill you do - its a little bit Shroedinger cat meets catch22

The thoughts of trying to search for a functional group in the origninal table is scary as there seems to be no consistency in the "extra info" / "aliases" column, and they are quite large fields in thier own right.

I think in the DBase at the NIH where I get the flat files the values are held in an ENUM (as the field is bar delimited). However my experience with ENUM is currently non-existent. I have though about creating an enum field on a couple of occasions, then decided that there would be no advantage in making this particular piece of code to split the values out!

During the day today I was in fact thinking about normalisation between some of my tables.

But the thought that as I only cross between primary keys in any given table column (or if not primary key another index column value) creating a linking table that contained just 2 or maybee three column didn't seem to make much sense.

From how I understand it, creating these linking tables and then "joining" them with the function of foreign keys is a bit like creating one great big table to search across.

I did do this for something, and then did a search across the 4 tables.... my results table has 16 * more entries than the total of all the tables put together. I was finaly able to work out that this was due to the query recursively searching each table, with each value in each other table (due to the foreign key), but couldn't find a way to stop if from doing so! the stange thing in this situation was, when I did a basic search it was OK (ish) but if I decided to put a 
```
 create table as....
``` or a ```
create view as
``` at the start of the statement suddenly I quadrupled the number of search results! In the end I did essentialy the same as I did on this occasion. Dropped the foreign keys and then created intermediary temporary tables holding just my values of interest, then cross referenced these much smaller tables (each of between 50 and 300 entries).

Its an interesting issue having all this data pre pared for you, I can now prety much write <load data infile...> commands on the fly. But I still prefere to use
[code[
select * from tableName1
where value in (select from table2);
[/code]
as opposed to trying to use join statements, which when I use them never seem to give me the results I was hoping for!

David.

---

### Post by kidders on 2009-02-20
Drat... so you *have* been through all that already, and you *do* know all the angles. :-( I was afraid of that.

Sorry I haven't been able to help you ... it looks like your dataset is just too large to make practical use of any of my suggestions. The only ideas I have left relate to aspects of MySQL (and your data) that I don't know that much about ... for instance, whether MySQL supports different types of indexes (eg bitmap vs b-tree), and whether your data lends itself more to certain indexing strategies than others. There's not normally a reason to care about issues like that (ie shaving nanoseconds off query execution times), but in your case, there could be significant benefits.

Anyhow, perhaps you should try posting your question again ... someone who's run into these kinds of problems before might pick it up next time!

---

### Post by theDaveTheRave on 2009-02-21
kidders


Like you I don't know all the angles and how to implement their solutions (see what I have said above regarding "normalising") the tables.

Once I get down to the teams data (which is about 500 or so) the searches are nice and quick.

If you go onto the NCBI web ite and do a search, you will see how long their system takes (here is the [site]("http://www.ncbi.nlm.nih.gov/sites/entrez")), in the box at the top drop in the following search string 188480 then click GO.

On the NCBI site this search is almost insant, on my 3 year old Acer 3680 laptop, it takes me just under 2 minutes.

So I guess that isn't a bad comparison, considering their servers must be a little bit more powerfull than my little laptop!

The other search that I did was a little more "complex" and getting the required data from the NCBI site would probably have involved a number of different searches, and lots of navigating between pages etc.

All in all I think the performance of my install MySQL isn't too bad in comparison!

My boss did say something funny when I was doing the original search for him, "maybee this is a limitation of MySQL over Filemaker Pro"

I didn't like to point out that just loading one of these BIG data tables in FileMaker caused my works desktop to stop working for 15 minutes - and that was "viewing" the table in MySQL, who knows how log it would have been had I wanted to "search" do a cross reference!

Maybee I shouldn't have kept my mouth shut!

Maybee I should load the 2 tables I was searching for into an FMP file, create the "view" that will work as the query, and then do the same search?

Will be a good benchmark for him.

Somehow I don't think it will perform very well...

In fact, as part of a MySQL query can I have it create another table as the sub query (ie like my original question, but the subquery first creates a new table with its results), or should I just run the queries in quick succession - a bit like a stored procedure? I may put this question into its own thread.. what do you think?

David

---

