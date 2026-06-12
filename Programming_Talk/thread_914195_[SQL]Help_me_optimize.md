---
title: "[SQL]Help me optimize"
date: 2008-09-08
forum: Programming Talk
---

### Post by themusicwave on 2008-09-08
Hey everyone,

I've been working on a reporting application here at work to report material usage for plastics processing facilities.

Basically, every time a machine finishes a material run some data gets dumped to a table in the database.  Right now it is all just going into one big table.  

However, I need to store up to 1 year's worth of data for as many as 64 machines.  They can complete a run in anywhere from several minutes to 3 seconds.  This means I could be looking at as much as 6,054,912,000 records per plant.  I'm not sure if I really want a table getting that huge.  That is 6.1 BILLION records.

In Addition, I have 5 filters that can be used on the data in any combination.  This gives a lot of power to the user to really break down their process.

Now my problem is that I am not sure how well this all scales.  My current idea for the reporting is to view it as a permutations problem.  Each of the filters pertains to a column of the tables.  For my reports I need every permutation of those columns.

I have an algorithm to generate these, but the amount of permutations becomes daunting very fast.  I ran 3 test machines over the weekend and I already have almost 750 permutations when I apply all my filters, if I tried this with a years worth it would be millions of queries, probably billions.

For each of these permutations I run 1 query to get the material usage information for that line of the report.

Everything works, but I would love to speed it up somehow.  I understand that when running millions of queries on billions of records, things could take quite awhile.

One important note is I am using the latest version of PostgreSQL and a Java SE application, also the latest version.

Each facility will buy 1 system to run my application.  They are cheap so they will be wanting a standard windows XP machine or maybe even Vista Business(Lord help me).

So what can I do to make this all faster?  I'm not looking for miracles, but anything to help would be great.

Thanks!

---

### Post by mujambee on 2008-09-09
If I read you right, you want report on material usage for every line, filtered by 5 fields.

You can trade space for speed and have summary tables that store sumed up info: just add a table with only those 5 fields as primary key and a sum field that stores the total material usage for the year. Whenever you write to your main table you also write to the summary one in the same transaction.

I don't know about PostreSQL, but in Oracle I would write post insert/update/delete triggers that keep both tables in sync.

Hope this helps

P.S.: If they are cheap, why spend money on a Win license? Linux is far cheaper than that ;)

---

### Post by themusicwave on 2008-09-09
I should also add that their is a sixth filter different from the others.  It is a time range filter where they can pick a time and date range for the report.

So for example start: 8/22/2008 16:52:45 End: 9/9/2008 8:0:5

How would that fit into a summary table?

I am thinking perhaps of doing something where I have summary tables for each month perhaps?

---

### Post by mujambee on 2008-09-09
> **themusicwave said:**
> I should also add that their is a sixth filter different from the others.  It is a time range filter where they can pick a time and date range for the report.

So for example start: 8/22/2008 16:52:45 End: 9/9/2008 8:0:5

How would that fit into a summary table?

I am thinking perhaps of doing something where I have summary tables for each month perhaps?

If they need reporting by the second then a summary won't help, but there might be a compromise:

[LIST=1]
[*]Define a minimum reporting timeslot: bigger timeslots allow for faster reporting; and add a sixth field to your primary key. From-to range should be defined using that time unit. Try storing dates as ordered ints (i.e.: Sept-08 would be 200809 or 809).
[*]Provide a fallback. Allow them to report on exact dates if need be, but warn them that will be much slower.
[*]If there are some fields that will be almost never used for filtering you might gain by adding a second summary table without those fields. If they don't specify that filter when obtaining a report go for the faster table.
[/LIST]
From personal experience I can advice on telling your customer that you won't start optimizing reports until at least 6 months of data have been recorded, anything you do beforehand will be just guessing.

I'm really an Oracle expert, and there you have something that is called partitioning. If you have a field that will have only a handful of values, Oracle would partition the table by that value, so you end up with as much tables as possible values that field can have. If PostgreSQL has something similar to that it would also speed things up.

On indexing: Be careful with that. Many people believe that adding more indexes will be faster, but on most cases an index too much will render your query slower, not faster.  Start indexing by your most selective fields (those with more different values), and test a lot. Also consider all possible types of indexes for each field.

P.S.: The concept behind summarys and indexes is to pre calc as much as possible on insert/update, so when you go to select there is a lot of work done. Don't be afraid of that, you have 3 seconds and that is a LOT of time.  And even if that is not enough, you can insert on a queue and have a background process to do all the math.

P.S. 2: Find out how your DB engine will execute your queries, and lay out your query according to that. Reorder your where clause and see what happens (say your filter is *where field1 = a and field2 = b*, try that and then try *where field2 = b and field1 = a*, stupid as it sounds, executing selective fields first will reduce the amount of data that goes to the next stage)

---

### Post by themusicwave on 2008-09-09
Thanks for the suggestions so far.  I am not a DBA I am just a developer.  But being the only developer I need to play DBA here as well.

I've been using Netbeans to profile the application all morning to find bottle necks in my Java code.

I did make one huge performance gain.  I changed how I connect to the database.  I know have a static persistent connection for reports.  So they only connect one time.

I shaved several seconds off my execution right there.  My application used to spend 12% of its time in my connect function, now it spends 1.2%.  So that is a big Bonus.

The application is spending about 93% of its time in my executeQuery function.  So clearly speeding up my queries would give  a huge performance gain.  The profiler reports that executeQuery was called 2,247 times and took 913 seconds.  This means each query is averaging .4 seconds.  I have no idea if this is good or not.  I doubt it, considering that I only have 125,000 rows in the database.

Postgres does have partitions and indexes, I need to look into them some more.  They may be able to help.

I'll look into your suggestions.  Thanks!

---

### Post by mujambee on 2008-09-09
> **themusicwave said:**
> The profiler reports that executeQuery was called 2,247 times and took 913 seconds.

I don't like that. Try grouping your queries, and execute fewer queries that get more data each time.  Bear in mind that executing a query goes trough a preparation phase prior to actually traversing the tables (parsing the statement, looking for indexes, reserving memory, deciding how to execute...). If your query returns only a handful of values, you spend more time preparing to execute than actually getting data.


> **themusicwave said:**
> considering that I only have 125,000 rows in the database
> **themusicwave said:**
> This means I could be looking at as much as 6,054,912,000 records per plant

In other words, you are spending 15min to test on 0.002% of your expected data. That gives us a rough 512 days for the final report. You'll need to optimize that by a factor of 1000 if you want your reports to execute in half a day.

---

### Post by themusicwave on 2008-09-09
You also have to keep in mind I have the overhead of the profiler, netbeans, Outlook, God awful McAfee and I am on an 8 year old PC that has less than 1 GB of RAM....

<Rant>
McAfee drives me insane it is set to scan every file I try to read or write. When our IT guy installed it I tried to get him to select the option "Maximize computer performance", instead he ticked "Maximize computer security".
</Rant>


When I don't run the profiler the application runs MUCH faster.

I have been experimenting with changing the ordering of my WHERE clause.  It can reduce the query in about half when done right.

Now I just need to figure out the optimal order.  If I understand right I want the first WHERE filter1=value1 to be the most specific one, or the one that returns the least rows.  I then want them to get less specific as I go.

---

### Post by mujambee on 2008-09-09
> **themusicwave said:**
> You also have to keep in mind I have the overhead of the profiler, netbeans, Outlook, God awful McAfee and I am on an 8 year old PC that has less than 1 GB of RAM....

That, in fact, is good news :D. I hope your customer understand the need for a really fast machine with huge ram and lightspeed hard drives.


> **themusicwave said:**
> 
McAfee drives me insane it is set to scan every file I try to read or write. When our IT guy installed it I tried to get him to select the option "Maximize computer performance", instead he ticked "Maximize computer security".
That's one of the many reasons that most DB's are run on Unix. ;)

For a development phase I would advice on disabling antivirus software. Unplug your machine from the network if that is giving them trouble.

> **themusicwave said:**
> 
Now I just need to figure out the optimal order.  If I understand right I want the first WHERE filter1=value1 to be the most specific one, or the one that returns the least rows.  I then want them to get less specific as I go.

Not exactly, in Oracle you put your most specific one the last, the parser reads lines from the bottom up. Find out how your DB engine handles this. Indexes may alter that order, so you only know for sure by testing.

---

### Post by mujambee on 2008-09-09
> **mujambee said:**
> I don't like that. Try grouping your queries, and execute fewer queries that get more data each time...

Re reading gives me the impression that I didn't explain it right. What I don't like is the fact that your query is executed 2,247 times...  That means going trough the preparation phase for that many times. If you get more data per execution you'll need to prepare less times and save that on execution time.

---

### Post by themusicwave on 2008-09-09
Each of those is a different query that is needed for the report.

To clarify here is how it works on a simplified scale:

Table has columns:

Machine Name, text - stores the name of the machine the record is from.

Operator, text - The name of the person operating the machine when record was recorded.

Order, text - The order running on the machine when record was recorded.

Timestamp - when the record was recorded.

Total - the amount of material use for this record.

Ok so my user now says they want to view data with the following break downs:

Machine Name
Order
Operator

From here the report will be generated, it will have one line for each permutation of the fields to view.  They are sorted by the order they are requested.

So, for each row of the report I end up with 1 query to get the total for that row.  Basically I end up with something like:

Query 1:
SELECT Sum(total) FROM table WHERE machineName=name1 AND order=order1 and operator=operator1

Query 2:

SELECT Sum(total) FROM table WHERE machineName=name1 AND order=order1 and operator=operator2

Query 3:


SELECT Sum(total) FROM table WHERE machineName=name1 AND order=order2 and operator=operator2

And so on....

That is the reason I have so many queries.  Previously I was trying to just grab larger groups of records and somehow tally up totals for each permutation.  This was a very long process.

In reality I have about 103 columns in the table.  I only use the majority of them in specific cases, and I am wondering if I should perhaps make a small table that contains only the few items I need for the big reports.  Maybe that would be faster?

Also,  I wish I could turn off McAfee, but my machine is locked down.  Yes, I am a software developer with a slow old locked down machine.....

It has to be Windows because my company is afraid of anything else....part of why I wrote it in Java is to easily port it to Linux someday.

---

### Post by mujambee on 2008-09-09
Why not?

```

SELECT machineName, order, operator, Sum(total)
  FROM table
  GROUP BY machineName, order, operator
  ORDER BY machineName, order, operator

```and get running.

and, if that is a fixed report, create a summary table with those fields as PK.

BTW, order is not a valid name for a column (its a SQL reserved word). Is that a valid column name in your DB?

---

### Post by themusicwave on 2008-09-09
I added 4 indexes to my table, one for each of the columns I filter on(filter 5 uses a combination of columns one of which is the timestamp).

Before the indexes, my typical query took 913ms to run.  It now takes 190ms to run.  This is quite an improvement.

Once strange thing I noticed is that if I run the same query a few times the tie taken changes.  It can range from 190-250ms.  Not sure why.

---

### Post by themusicwave on 2008-09-09
> **mujambee said:**
> Why not?

```

SELECT machineName, order, operator, Sum(total)
  FROM table
  GROUP BY machineName, order, operator
  ORDER BY machineName, order, operator

```and get running.

and, if that is a fixed report, create a summary table with those fields as PK.

BTW, order is not a valid name for a column (its a SQL reserved word). Is that a valid column name in your DB?

I actually called the column ordernumber so it is ok.

In addition to those easy filters I have 1 other filter that is somewhat evil.  It's a production shift filter.

A production shift is a combination of Day of the week and start and end time.  Like So

Late Shift A: Start 0:00:00 end 8:00:00 Days:MWF
Late Shift B: Start 0:00:00 end 8:00:00 Days:TR
Day Shift A: Start 8:00 end 5:00 Days: MWF
Day Shift B: Start 8:00 end 5:00 Days: TR

In my table I store the a timestamp with date and time, I also store just the time and the day of the week the record was created on.

I then need to query to pull out only the records that fall into that time range and days of week.

I also build a query for all the record that don't fall in any shift.

In the future I will have other filters like this that aren't a simple mapping of column -> value.  So I don't know how this will hold up then.

I'll look into it certainly though.

---

### Post by themusicwave on 2008-09-09
I tried the GROUP BY and ORDER By method just know and realized why I didn't go by it in the first place.

It doesn't actually return all the permutations of that set of columns.

It returned only 9 rows.  But I know I have 2 distinct values for machine name, 6 for ordernumber and 6 for operator.  That means there are 72 permutations.

After trying it I remembered that I originally had the exact same idea and ran into this same issue.

It was a good suggestion though

---

### Post by mujambee on 2008-09-09
version 1.1
```

SELECT machineName, ordernumber, operator, Sum(total)
  FROM (
        SELECT machineName, ordernumber, operator, total
          FROM data_table
         UNION
        SELECT machine.name  as machineName,
               orders.number as ordernumber,
               operator.id   as operator   ,
               0             as total
          FROM machine, orders, operator
       )
  GROUP BY machineName, ordernumber, operator
  ORDER BY machineName, ordernumber, operator

```Yes, there is a union and a double product of tables. You've probably been warned against both, but in this case it is advisable to do it this way; You'll try all combinations yourself, so let the DB do it, it is faster than you. Just a bit of advice, if any of your three tables gets out of control (probably orders), you'll get into trouble because the table product will get out of control.  Only problem with this approach is that it will eat your RAM away; you will need a good memory tuning on your DB to do this.

As for the shift, the easiest way usually is just compute it on your java side and put it in a new column.

Anyhow, remember that anything you do right now is only first approximate, you won't know till you test on real data with tons of values.

Try talking your boss into a test run without that antivirus, if you get a real performance gain, he'll be happy to eat 10 min on each test, instead of 15 (just my point of view as team manager).

---

### Post by themusicwave on 2008-09-10
> **mujambee said:**
> version 1.1
```

SELECT machineName, ordernumber, operator, Sum(total)
  FROM (
        SELECT machineName, ordernumber, operator, total
          FROM data_table
         UNION
        SELECT machine.name  as machineName,
               orders.number as ordernumber,
               operator.id   as operator   ,
               0             as total
          FROM machine, orders, operator
       )
  GROUP BY machineName, ordernumber, operator
  ORDER BY machineName, ordernumber, operator

```Yes, there is a union and a double product of tables. You've probably been warned against both, but in this case it is advisable to do it this way; You'll try all combinations yourself, so let the DB do it, it is faster than you. Just a bit of advice, if any of your three tables gets out of control (probably orders), you'll get into trouble because the table product will get out of control.  Only problem with this approach is that it will eat your RAM away; you will need a good memory tuning on your DB to do this.


Honestly I am not all too familiar with Union.  Could you break down what this query is doing for me?  I want to fully understand how it works.

Also, right now ordernumber is in the datatable.  There is no orders table.  How would this change the query?


> **mujambee said:**
> 
As for the shift, the easiest way usually is just compute it on your java side and put it in a new column.


I had thought of this, the trade off is that if my customer suddenly decides that he wants to rename a Shift or adjust it's time then I have to go through the entire database and update it to reflect this.  I was afraid this would require some huge update.

However, I am liking the idea a bit more now, especially since it would be much easier on the SQL side than my current approach.  It would also then be possible to index on this column, so each filter could have an index.

For example, right now I append this to the where clause for a shift:

```
(  (time >='00:00:00' AND time < '08:00:00')  AND ( dayofweek='Monday'    OR  
dayofweek='Wednesday'   OR  dayofweek='Friday' ) ) 
```

That would find all the records that fall into that specific shift.  This particular shift is on MWF from 0:00-8:00.

> **mujambee said:**
> 
Anyhow, remember that anything you do right now is only first approximate, you won't know till you test on real data with tons of values.


I do understand, but my company doesn't really.  We are not a software company we are an Equipment manufacturer.  They don't understand how software differs from building a motor for example.  The challenge is I may never get my hands on such data.

> **mujambee said:**
> 
Try talking your boss into a test run without that antivirus, if you get a real performance gain, he'll be happy to eat 10 min on each test, instead of 15 (just my point of view as team manager).


I have dicussed it with him, and IT is pretty much the law.  Being that I am a special case they give me some privledges, but not many.  I do have a test machine without AV, but it is dedicated to testing another system.  I might be able to test this on it as well.

I do appreciate all the help.  As I've said I know just enough SQL to get by really, I basically am relying on 2 college courses in databases to figure all of this out.

Thanks!

---

### Post by themusicwave on 2008-09-10
I think my method will need to change.

I ran a test today where I inserted rows until my data had a few hundred thousand permutations.

When I ran my report it got to about query 87,500 and the JVM ran out of memory...

so perhaps one big query is the way to go.  Although my JVM only has 128mb allocated, and probably will need much more.

---

### Post by mujambee on 2008-09-10
> **themusicwave said:**
> Honestly I am not all too familiar with Union.  Could you break down what this query is doing for me?  I want to fully understand how it works

From inner to outer:
```

SELECT machine.name  as machineName,
       orders.number as ordernumber,
       operator.id   as operator   ,
       0             as total
  FROM machine, orders, operator

```This is a cross product of tables machine, orders and operator. As you may notice, there is nothing that links them, so the DB engine won't know how to associate rows from one table with those from the other. The solution is to combine all with all, say you have machines M1 and M2; and operators O1, O2 and O3; we will forget about orders for this example. A cross product of tables machine and operator would give you the pairs M1-O1 M1-O2 M1-O3 M2-O1 M2-O2 M2-O3. A second cross product with orders would give you the whole set of combinations of those three columns. The last column, total, is there just for completeness, we will come to this later.

Now for the UNION. A union is basically an append of queries. If you have several queries that return the same set of columns (names and data types), you can use unions to get all results in the same result set.  i.e.: say you have this data on your table (forget about orders for now):
```

machine operator total
------- -------- -----
M1      O1          20
M1      O1          10
M1      O2          11
M2      O1           1
```A union with the previous cross product, would return all this colums
```

machine operator total
------- -------- -----
M1      O1          20
M1      O1          10
M1      O2          11
M2      O1           1
M1      O1           0
M1      O2           0
M1      O3           0
M2      O1           0
M2      O2           0
M2      O3           0
```Notice that you now have all posible machine/operator combinations with a 0 total plus all existing combinations with their real totals.

Wrapping that query in brackets will turn it into a "virtual table" (not sure if this is standard SQL), so you can select from it; the group by you already knew about...

> **themusicwave said:**
>  Also, right now ordernumber is in the datatable.  There is no orders table.  How would this change the query?

Mmmmmm, its too late over here right now and the kid is giving us a hell of a night. I'll think about it tomorrow morning and try to post something before you get to work. An initial idea would be to have a "giding query" on orders and try to match that to a cross product on machines and order numbers, using an *outer join*; but right now I just can't get into it. Sorry. :(

> **themusicwave said:**
> I had thought of this, the trade off is that if my customer suddenly decides that he wants to rename a Shift or adjust it's time then I have to go through the entire database and update it to reflect this.  I was afraid this would require some huge update.

Not sure about the USA, but in Europe that would be extremely rare, I've never seen a company change their shifts. Probably a nightmare of changes in payments, all software must be changed, labor union....  i wouldn't worry about that.

> **themusicwave said:**
> For example, right now I append this to the where clause for a shift:

```
(  (time >='00:00:00' AND time < '08:00:00')  AND ( dayofweek='Monday'    OR  
dayofweek='Wednesday'   OR  dayofweek='Friday' ) ) 
```

```
time < '08:00:00'  AND dayofweek IN ( 'Monday', 'Wednesday', 'Friday' )
```Time will always be >=0 ;)

> **themusicwave said:**
>  I do understand, but my company doesn't really. We are not a software company we are an Equipment manufacturer. They don't understand how software differs from building a motor for example.

Actually, it is very similar. Ask them if they test their equipment with a token load of 100Kg or with real loads of 10Tons.

I understand you provide control software for machines your company will build. Is that it?. If your customer is big enough, they probably have some process control software in place. If there is a good PIMS there, they have really powerful DB engines specifically designed for the task of storing huge amounts of linear data and reporting on it. Interfacing into that would be easier and faster than anything else. Just check. OSISoft's PI, Honeywell's PHD and Yokogawa's Exaquantum PIMS are top of the class in this area.

> **themusicwave said:**
> The challenge is I may never get my hands on such data.
That is something you must make them understand. If you can't refine your reports on real data, they will end shutting down your system in two/three years time, and that is a shame on your company and on you. (It happened to me once, you won't like it).

---

### Post by mujambee on 2008-09-10
> **themusicwave said:**
> so perhaps one big query is the way to go.  Although my JVM only has 128mb allocated, and probably will need much more.

Big queries get hard on your DB memory, not on your process. Your problem is that you are compositing that amount of data in place, try throwing it to a file as soon as you get it.

---

### Post by mujambee on 2008-09-11
> **mujambee said:**
> Mmmmmm, its too late over here right now and the kid is giving us a hell of a night. I'll think about it tomorrow morning and try to post something before you get to work. An initial idea would be to have a "giding query" on orders and try to match that to a cross product on machines and order numbers, using an *outer join*; but right now I just can't get into it. Sorry. :(

I was thinking in SQL and only in SQL. As we have a Java client that can have some logic, there is a much better approach, using arrays to store temporary data. My idea is to have a local array of machines and operators, and use a simple query to get only relevant data from the DB. It will not have all combinations of order/machine/operator, but you can provide that on your Java side.

Here it goes:

1. Create an array with all combinations of machine and operator, just issue the following SQL to the database and store it in a bidimensional array:

```
SELECT machine.name,
       operator.id
  FROM machine, operator
 ORDER BY machine, operator
```

2. Select all relevant data from your table:
```
SELECT machineName, order, operator, Sum(total)
  FROM table
  GROUP BY machineName, order, operator
  ORDER BY order, machineName, operator
```
(notice that the last items of our ORDER BY are the same, and in the same order, that those in query No 1).

3. You'll need a "current machine/operator" and a "current order number". We will call this CMO and CON, it's shorter.

4. Loop trough the result of this last query. For each row:

  A. Check if CON has changed. If so, report a line with your CMO, older CON and total=0. Repeat until you run out of COM's.

  B. Check if row's machine/operator comes later than your COM. If so, throw lines with your CON, COM and a total of 0 and increase CMO untill you catch up.

  C. Report the row you'v just read.

---

### Post by themusicwave on 2008-09-11
I have changed the shifts so now when batches are inserted they store shift name they fall into.  The names are the primary key of the shifts table.

I also added code that if/when they change a shift it updates the entire database.  I did this just to be safe and I do warn them about how this will take some time before they do it.

I also added another index to the database on my new shift column.  My queries are now running in the 80ms range. When I use my whole "One query per report row thing".

I also realized on the way home yesterday that the database wasn't the memory overflow, the fact that I was storing all my pre generated queries is the over flow.

Basically the way my program works is this:

Figure out all the distinct values for each of the columns I am going to show such as operator, machine, order.  Store each of those in and ArrayList(like an array).

Now make a new ArrayList with every permutation of those values.  Store that.

Then step through that an generate a query for every permutation and yet again store that.  This is where it explodes.  Storing thousands of 200-300 character strings.

Then run each query and store the result to you guessed it another array, called the output array.

Finally step through the output array and output all the values to OO.org.


I think I need to go about this that doesn't store so many massive arrays.

Basically I am going to generate the next permutation store it in a temp var.

Generate the query for it store it in a temp var.

Generate the output line store it in a temp var.

Output the line.

This way instead of storing thousands of things in RAM I will only store 4.

However I am still not sure it will be fast enough...

If my calculations are correct, then 1 Billion queries running at 80ms each would take years to finish....Heck even 10,000 queries would take 13 minutes....I doubt that is acceptable to anyone...

I need to reread what you posted and try to see how it applies to my schema.

Until then, my Schema looks like this:

Batches - Big table with the data

Columns:
total, shift, operatorname, machinename, ordernumber

Shifts - stores shift definitions

Columns: name, starttime, endtime

machines - machine info

columns: name, ipaddress, location

There is actually no table for operator or orders, they are merely numbers input into the machine that mean something to the customer.  All I do is store whatever the machine had in that field at the time.


So form there I need to apply the UNION to get all the permutations of:

machinename, ordernumber, operatorname and shift

Right now I am going to concentrate on figuring out how the SQL should work, from there I can write the Java.

I'll let you know if I get anywhere.

Thanks again!

---

### Post by themusicwave on 2008-09-11
I think I am getting very close!

How does this look:

```

SELECT  machineName,ordernumber,shift,sum(total) FROM
	(
		SELECT 
			machines.name  as machineName,
			batches.orderNumber as ordernumber,
			shift.name   as shift,
			batches.totalweightall as total
		FROM machines, batches, shift
        ) data_table
        GROUP BY machineName,ordernumber,shift
        ORDER By machineName,ordernumber,shift

```

The data_table there is an alias.  Postgres requires an alias for all subqueires.

I think this works well.  Running it produced exactly 6,030 results.  I calculated the permutations my old method would have generated and it is exactly 6,030.  It looks like every permutation is here.

Also, with my indexes in place this query took about 28 seconds to run with a database of 200,000 this is a vast improvement.  My previous method would have take about 482 Seconds.  This means this method is roughly 17 times faster!

I'm going to continue to experiment.  I don't actually think I will need a union at all, a sub query seems to do the trick.

I also think I may add a HAVING clause to filter out rows that have a total of 0, those don't need to be shown on the report.

Thanks again!

---

### Post by themusicwave on 2008-09-11
Thanks once again for all the help.

I had an additional question about filtering my data.  For example, the batches table with all the data has a column called datetime that is a timestamp.

I need to filter on it so that users can select date ranges.  I think this can be done in the subquery.  Additionally, I don't need to process any permutations that have a total of 0, so I added a HAVING clause to remove them.  And finally I need to be able to filter on the various fields like shift.

So I am thinking this will give me only records in my specified time range that have a total >0 and have the shift 'Day Shift'

```

SELECT  machineName,ordernumber,shift,sum(total) FROM
	(
		SELECT 
			machines.name  as machineName,
			batches.orderNumber as ordernumber,
			shift.name   as shift,
			batches.totalweightall as total
		FROM machines, batches, shift
                WHERE datetime BETWEEN '2008-8-1 0:00:00' AND  '2008-9-12 0:00:00'

        ) data_table
        GROUP BY machineName,ordernumber,shift
        HAVING sum(total) > 0 AND shift = 'Day Shift'
        ORDER By machineName,ordernumber,shift

```

Does this look correct?  Thanks.

---

### Post by mujambee on 2008-09-12
> **themusicwave said:**
> I think I am getting very close!

How does this look:

```

SELECT  machineName,ordernumber,shift,sum(total) FROM
    (
        SELECT 
            machines.name  as machineName,
            batches.orderNumber as ordernumber,
            shift.name   as shift,
            batches.totalweightall as total
        FROM machines, batches, shift
        ) data_table
        GROUP BY machineName,ordernumber,shift
        ORDER By machineName,ordernumber,shift

```The data_table there is an alias.  Postgres requires an alias for all subqueires.

I think this works well.  Running it produced exactly 6,030 results.  I calculated the permutations my old method would have generated and it is exactly 6,030.  It looks like every permutation is here.

Bad, it looks bad. ;)

It is a cross product of tables macnines, batches and shift, which will give you all possible combinations of the three. Have you checked your sums? I bet you get the same sum(total) for all rows in your query.  You need to link the tables in a WHERE section (inside the subquery).

> **themusicwave said:**
>  Also, with my indexes in place this query took about 28 seconds to run with a database of 200,000 this is a vast improvement.  My previous method would have take about 482 Seconds.  This means this method is roughly 17 times faster!

Be careful with that, remember that too many indexes may be as bad as not having any.

> **themusicwave said:**
> I also think I may add a HAVING clause to filter out rows that have a total of 0, those don't need to be shown on the report.

I'm not sure I understand. Yesterday you told us you needed all permutations, now you don't need rows that have a total of 0. If this is the case, what's the problem with doing something like this:

```

SELECT  machineName,orderNumber,shift,sum(totalweightall)
  FROM BATCHES
 GROUP BY machineName,orderNumber,shift

```

---

### Post by themusicwave on 2008-09-12
> **mujambee said:**
> Bad, it looks bad. ;)

It is a cross product of tables macnines, batches and shift, which will give you all possible combinations of the three. Have you checked your sums? I bet you get the same sum(total) for all rows in your query.  You need to link the tables in a WHERE section (inside the subquery).


You are correct, I don't get the exact same total for every row, but they repeat in a cycle it looks like.

> **mujambee said:**
> 
Be careful with that, remember that too many indexes may be as bad as not having any.

I currently have 5 indexes, 1 for each of the 5 columns I can filter on.

> **mujambee said:**
> 
I'm not sure I understand. Yesterday you told us you needed all permutations, now you don't need rows that have a total of 0. If this is the case, what's the problem with doing something like this:

```

SELECT  machineName,orderNumber,shift,sum(totalweightall)
  FROM BATCHES
 GROUP BY machineName,orderNumber,shift

```


All the permutations would be fine, however I don't need to show permutations with a total of 0.  So if I can filter them out in the query it may be worth it.  If not, my Java logic can just choose not to output them.

Also, I think you need and order by on their to get them to come out in the correct ordering:

```

SELECT  machinname,orderNumber,shift,sum(totalweightall)
  FROM BATCHES
 GROUP BY machinnam,orderNumber,shift
 ORDER BY machinnam,orderNumber,shift

```
I think this does the trick, from here I can add any filters I needs for my 5 columns to a WHERE clause.  I also could add a HAVING to get rid of the 0 total rows I believe.

Like so:

```
SELECT  machinname,orderNumber,shift,sum(totalweightall)
  FROM BATCHES
WHERE machinename='machine1' AND orderNumber='334533' AND  datetime BETWEEN '2008-1-1 00:00:00'  AND  '2008-9-10 8:00:00'
 GROUP BY machinnam,orderNumber,shift
HAVING sum(totalweightall) > 0
 ORDER BY machinnam,orderNumber,shift

```

I think that should do the trick from there.  I don't think I need to do a cross product, since all this information is in batches already.  I think the real key I was missing was GROUP BY.  I had forgotten about it since my SQL classes, because I hadn't needed it.  

Does that look ok to you?  Once again thank you for all the assistance.

---

### Post by pmasiar on 2008-09-12
> **themusicwave said:**
> 
```
SELECT  machinname,orderNumber,shift,sum(totalweightall)
  FROM BATCHES
WHERE machinename='machine1' AND orderNumber='334533' AND  datetime BETWEEN '2008-1-1 00:00:00'  AND  '2008-9-10 8:00:00'
 GROUP BY machinnam,orderNumber,shift
HAVING sum(totalweightall) > 0
 ORDER BY machinnam,orderNumber,shift

```


First, you know by now that finetuning SQL is black magic :-)

I did not read whole thread, but code above might be one of the sources of delay: If you issue multiple queries, you don't want to put exact values to SQL, but put placeholders like this: machinename=? AND orderNumber=? prepare the statement and bind the real values when executing. 

One of DBA's tools you want to master is "show execution plan", whatever it is in your SQL dialect, which will tell you what indexes will be used (and where full search), so you can try different variants of SQL for same goal.

Also, if you have "ORDER BY machinnam, orderNumber, shift" make sure you have index with those fields in that order too.

---

### Post by themusicwave on 2008-09-12
> **pmasiar said:**
> First, you know by now that finetuning SQL is black magic :-)

I did not read whole thread, but code above might be one of the sources of delay: If you issue multiple queries, you don't want to put exact values to SQL, but put placeholders like this: machinename=? AND orderNumber=? prepare the statement and bind the real values when executing. 

One of DBA's tools you want to master is "show execution plan", whatever it is in your SQL dialect, which will tell you what indexes will be used (and where full search), so you can try different variants of SQL for same goal.

Also, if you have "ORDER BY machinnam, orderNumber, shift" make sure you have index with those fields in that order too.

Thanks for the info.  SQL is a strange strange thing.  As you can see it really isn't my strong suit.

I have played with Postgres's EXPLAIN option a bit.  I am still trying to decipher it's output.

Also, the problem with the index order is that the user will actually specify the order they want the data in.  So my ORDER BY and GROUP BY will get rearranged depending on that.  So I don't think I can do anything about matching index order to my ORDER BY.  I didn't even know indexes had an order....

---

### Post by pmasiar on 2008-09-12
> **themusicwave said:**
> Also, the problem with the index order is that the user will actually specify the order they want the data in.  So my ORDER BY and GROUP BY will get rearranged depending on that. 

They **really** want to make your life miserable :-)

Consider creating temp table from selection (using index), and then generating report from that temp table. If temp table is small enough DB is fast enough to get results fast even without indexes - faster than full search of all data. "CREATE TABLE as select from" is another of those tricks of trade you should have learned from DBA you don't have :-)

---

### Post by themusicwave on 2008-09-12
> **pmasiar said:**
> They **really** want to make your life miserable :-)

Consider creating temp table from selection (using index), and then generating report from that temp table. If temp table is small enough DB is fast enough to get results fast even without indexes - faster than full search of all data. "CREATE TABLE as select from" is another of those tricks of trade you should have learned from DBA you don't have :-)

I'll have to look into that.  Could you provide an example?

This is you typical "Software is magic" type of place.  So we have very little in the way of software developers.  I am pretty much it.  We have a few Electrical Engineers who write PLC code and that is it other than me.

It is also common to have things said like "I don't understand why X is so hard it's just software..."  I cringe every single time.  So they have no problem asking for hard/impossible things because they don't know it is hard.  They think it is "just software".  

They also don't allocate me much testing time at all because it is "just software and it's no big deal to fix it later".

Sigh....

---

### Post by pmasiar on 2008-09-12
```
CREATE TABLE suppliers
  AS (SELECT id, address, city, state, zip
          FROM companies
          WHERE id > 1000);

```
[http://www.techonthenet.com/sql/tables/create_table2.php](http://www.techonthenet.com/sql/tables/create_table2.php)

And you should consider looking for a place where you can learn from other smart people. I know how hard it is...

---

