---
title: "complex Execute method sending to MySQL"
date: 2008-12-10
forum: Programming Talk
---

### Post by theDaveTheRave on 2008-12-10
Hi all.

this is a question regarding MySQL function calls from a small stand alone Java proggy.

So far my proggy will happily do the folowing.

- find a file and test if it is newer than a previous one !
- if this file is newer
         - Create 2 new tables in 2 databases, based on the file name & date.
         - executeUpdate() a <load data infile> call into the new table.

so now I have 2 nice new tables, the first with lots of data (4 million rows and 13 column...  in case you wondering).

The point of table 2 is to hold a limited selection of the first that we search more often - I know that I'm breaking lots of rules of normalisation etc, but my intention is to normalise table 2 at a later point. The tables are in fact in separate "Dbases".

So I want to select * from table one and insert into table 2. But I want to only select a certain number of records identified by a similarity in the Primay key between this first table and a third.

so in brief my SQL statemen is.

Select * from firstTable
where primary key in firstTable in (select primary key from thirdTable)

This gives me the results I would like so I create a MySQL query to insert

insert into secondTable
Select * from firstTable
where primary key in firstTable in (select primary key from thirdTable)

Again this works fine when hooked into the MySQL monitor.

So I re-create the whole process inside my program.

All goes perfectly up untill I attepmt to populate the secondTable.

I started out sending the SQL message as an executeUpdate() - as it was sending an update to a table. but soon realised that due to the fact I am performing a select also that this will fall down.

Research suggested I should use a <prepared statement> so i created one and tested, again failure.

Each time the error being reported was an SQL syntax error.

so I tested my query in the monitor just for sanity, and it worked.

So next I expanded the * catch all and input all the column names, but still I got the same error message.

More investigation lead me to try a similar method, but now using a straight <execute()> method in connectorJ.

To make life easy (supposedly!) I create this inside a new class (that I called "complexQuery") that just did the folowing:

created the required preparedStatement

created a connection to the dbase.

created various results sets to enable the control of the execute() statement.

Threw the required exceptions, that were then caught by the class that called / created this new "compledQuery"

and finaly sent the required message to the DBMS.

All seemed to be going just fine!

compilation worked, but when I ran the prog I get <exception in main>.

I assume a couple of possibilities to resolve this, but would like some advice either way (to help my understanding)

Should I throw and catch my exceptions in this new class?

should I use this new class to send the query first, collect a result set and then grab the results of this and stuff them into the new table I have for the results? - this seems long winded to me especially when the MySQL monitor is more than happy with doing both in the same command.

Your advice is greately appreciated.

If required I will post my class files here, I don't have them with me at the moment.

thanks for the help and advice.

David

---

### Post by mssever on 2008-12-10
> **theDaveTheRave said:**
> Each time the error being reported was an SQL syntax error.
Have you quadruple-checked to be sure that the SQL being sent is free of syntax errors? You can't solve a syntax error by wrapping it in a class and catching exceptions.

It would help if you posted a code snippet along with the exact error message.

---

### Post by theDaveTheRave on 2008-12-10
yes I did check the syntax, I ran the same thing in the monitor, copied it into a text file then added it into the programme.

I'm contemplating making it a stored persistent procedure, then seeing if it will work when called from MySQL and then the issue of "syntax" won't be an issue - as the command will be the same.

Dave

---

### Post by theDaveTheRave on 2008-12-12
OK so i've checked the syntax again.

originally I was using a string that was created from a number of variables, so I adjusted the string not to use those variables.

The query now does what it should, so there was an issue in my variables that I passed to the query string!

And appologies to mssever,

there was a syntax error, it was the lack of a space between a variable and the next word

eg, sample of code.
```

String table = "name of table"
String script = "select * from " + table +"where val = something"
```

so humblest appologies to mssever for having missed the lack of a space!

David

---

### Post by mssever on 2008-12-12
I've spent plenty time trying to figure out similar issues myself. One thing I find useful for debugging purposes is to print out the SQL string after all substitutions have been made. It can save a lot of time.

---

### Post by theDaveTheRave on 2008-12-15
mssever,

Hmm fair point, I guess we all live and learn (I just seem to learn the hard way.... often   ;) :lolflag:

I guess I couldn't see the wood for the trees on this occasion. copying and pasting the command into the MySQL monitor made it work, and I stupidly disregarded the fact that I had to edit out the portions that were variables??

god I had programming... the damn things allways do exactly what you tell them ):P

David.

---

