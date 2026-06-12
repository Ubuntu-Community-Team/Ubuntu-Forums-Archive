---
title: "Best SQL Query Scripting Language?"
date: 2007-06-12
forum: Programming Talk
---

### Post by SNYP40A1 on 2007-06-12
I need to run SQL queries and then do some processing on the queries. I have been using JMP and it certainly has all the built-in functions that I need, but I absolutely hate the scripting language.  It has plenty of useful built-ins, but also has some very annoying behavior such as not executing certain commands unless a RUN_ALLFUNCTIONS or similar statement is called in order to get everything up to that point to execute before proceeding to the lower statements.  There's some other stuff too, but I don't have time to go into it.  Anyway, I want something that:

1. Allows me to execute SQL queries.
2. Create a new column to be appended to the result of the above SQL query and allow the column to be defined by a function.  For example, the column might be a boolean or character assigned based on the results of the other column(s).  
3. Take 2 queries and join, matching by column name.
4. Allow for summary.  Take the table from above and group by one column entry and for that group summarize other columns by median, mean, or quantile.  For example, say I have one column called "Part" which is either a door, window, or stair.  For all doors, I want to know the mean or median height.  Same for all windows and stairs.  
5. Eventually I will get a bunch of numbers from the above operation and I will want to make a composite table out of all the entries.  For example, one cell in the composite table might be the median of height for all doors produced on a certain day (where cols would be by day).  

Any ideas?  I started playing around with both Perl and Python, I was able to pull SQL queries in both, but there are no built-ins such as join table or compute median that I am looking for.  Hopefully someone knows of smarter solution than JMP.

---

### Post by Tundro Walker on 2007-06-12
I don't have an answer, just want to clarify for others who might get confused by your thread title.

He's asking which programming/scripting language has a really good, simple, yet powerful SQL/Recordset library that isn't a pain in the butt to try to implement, so he can run SQL scripting through the programming language.

---

### Post by winch on 2007-06-12
> **Tundro Walker said:**
> He's asking which programming/scripting language has a really good, simple, yet powerful SQL/Recordset library that isn't a pain in the butt to try to implement, so he can run SQL scripting through the programming language.

I think he (she?) is asking for something different to that. I think he wants a database with an embedded scripting language where the scripting language doesn't suck. Something in the same vein as Access.

---

### Post by harun on 2007-06-12
All of that is trivial to implement in Perl. Being that you are brand new to it, it might take you a bit of work though. For joining can you just do that in the SQL? You didn't say which database you are using and if it is MySQL or Oracle (or just about any other one I know the name of) just do the joining in the SQL.

If for some reason you don't want to do the joining in the SQL or don't know how you could still do it in Perl. It would take a bit of learning but if you learn how to do that in Perl (and the other things you list) you will have a lot of really useful tools to add to your toolbox. I think the time spent would be worth it.

Feel free to post any specific problems we would be glad to help.

---

### Post by SNYP40A1 on 2007-06-12
Sorry for the confusion, but thanks for the help.

Maybe Perl is the best choice, but there are still some things lacking.  It does not quite have everything that I want, although I have only been using it for about 2 years now and not that often.  I mentioned in my previous post that I was able to pull my queries just fine using Perl, but after that I hit a roadblock.  It's not quite the SQL join that I am looking for, or if it is show me how.

Say I want to do something like this:

result = query.execute("Select day, parts, height, quality_rating
from somedb");

Onto the "result" table, I want to add a new column which summarizes the quality_rating.  If the quality rating, (let's assume it to be an integer that represents quality), is in the range 0-9, the new column corresponding to that row should contain an "A".  If quality_rating is in the range "40-49", then the cell in the new column corresponding to that row should be assigned "B" and so on...  Let's call this new column "Type".

Now I want to take that table and produce a new table that contains all the median of all "height" grouped by "day" and "Type".  

Now I take the "result table" and produce another table that just has median(height) grouped by day.  

I then join the two tables matching on "day" so that I have a new table with "day", "type", [median of height by day and type], [median of height by day]

I then say that for each row, I want to divide [median height by day and type] by [median of height by day] to get some ratio.

Basically, I do want to do GROUP BY and JOIN, but some other stuff as well.  I need mean, median, and quantile functions (I know that SQL supports the AVG function when combined with GROUP BY).  I also want to be able to append to a SQL result table a new column and assign values into the new column based on the other columns.  So I think what I need is slightly more than SQL.

---

### Post by SNYP40A1 on 2007-06-12
Also, I forgot to mention, I am using Oracle DB.

---

### Post by Tundro Walker on 2007-06-12
Ok, now that makes sense.

You can do all that in your SQL statements.  In SQL, pulling fields basically has the following syntax...

```
SELECT <value> as <new field name>

... or ...

SELECT <new field name> = <value or expression that returns a value>


```

...so, you could do 

'12' as 'twelve' ... or 'twelve' = '12' ... which would create a new column and populate it with 12 for each value returned on your rs.

Null as 'null_column'  ... which would create a new column with Null values.

'' as 'blank_column' ... which would create a new column with zero-length strings.

As example, let's say you had a table called "blah" that had 50 records in it...

```
SELECT *, '12' as 'twelve', 'null_col' is Null, '' as 'blank_column'
FROM blah
```

That'd pull all fields from "blah", and add 3 additional columns the the returned rs, 'twelve' which had '12's in it, 'null_col' which had null values in it, and 'blank_column' which has zero-length strings.

Using this format, you can use IF statements and such to judge values in other columns to fill in a new column on the return recordset. I don't know the exact syntax (you'll need to google a good SQL reference), but you could do something like...

> case 'test_score_field'
  < 70 then 'D'
  < 80 then 'C'
  < 90 then 'B'
  else 'A'

Again, that's not the exact SQL syntax, but you get the idea.  You can group things based on values.

Note that one pit-trap you should watch out for is that you can't cascade calculated fields into other calculated fields in the same SQL.  It's easier to explain this with an example.

Let's say I pull a column called 'Add' = 1+1.  I then want to take that result and use it in field 'Multiply' = 'Add'*2.  But, that won't work.  Reason being, when the SQL runs, 'Add' is being calculated at the same time 'Multiply' is being calculated.  'Multiply' doesn't have anything for 'Add', so it errors.  To do something like this in one SQL pass, you'd have to manually fill in the 'Add' values into 'Multiply'.  So, you'd have 'Add' = 1+1, 'Multiply' = (1+1)*2.

It looks like that's what you're wanting to do on some of those columns, and I think you can do it all in one pass instead of running an rs (recordset) out as a table, then running it again, and again and again to add more columns on it.  You should be able to do it all in one SQL statement, you just can't use a calculated column inside another calculated column at the same time.

As for joining, SQL used to make it where you listed the tables in the FROM part, then the joins in the WHERE part.  But more recent SQL syntax does the following...


```
FROM <table1> as <alias> (nolock)
  (INNER / OUTER / RIGHT / LEFT) JOIN <table2> as <alias> (nolock)
      ON <table1 alias>.<key> = <table2 alias>.<key>
               AND <table1 alias>.<key2> = <table2 alias>.key2>
```

So, the first table just goes in normally, but each subsequent table gets some kind of "JOIN" statement proceeding it, followed by some "ON" statement to let it know what columns join as keys.  The (nolock) is used to keep from locking the table...in other words, if you just want to pull info from it, but not write to the table.  This is useful if you're working in an environment where folks are writing to a table (EG: at a company that is constantly updating customer info), and you're just wanting to tap some info quickly.

This is easier if you see an example.

Let's say I have table Cust_Info with customer names and stuff, and I want to link it to Cust_Address, which has customer addy info.  They're one-to-one joins, 1 customer to 1 address.  They join on the Cust_ID field...

```
SELECT ci.Last_Name, ca.City
FROM Cust_Info as ci (nolock)
  INNER JOIN Cust_Address as ca (nolock)
      ON ci.Cust_ID = ca.Cust_ID
```

Note that even though each field pulled is probably unique to each table, I still qualify them with their table aliases, just in case any tables share fields.

If you have a situation where tables join via two keys, then you'd add the AND part after the ON.  It's hard to think of examples, but where I work, there are some cases.  We use a CUST_NO & CUST_ID to differentiate customers on some systems.  And, there's BILL_ITEM_ID, and other identifiers.  In rare cases, I have to join two tables via a CUST_NO & a BILL_ITEM_ID.  EG:

```
SELECT T1.*, T2.*
FROM TABLE1 as T1 (nolock)
  INNER JOIN TABLE2 as T2 (nolock)
      ON T1.key1 = T2.key1
      AND T1.key2 = T2.key2
```

This can get even more annoying when the two fields join to different tables.  EG:

```
SELECT T1.*, T2.*
 FROM TABLE1 as T1 (nolock)
   INNER JOIN TABLE2 as T2 (nolock)
       ON T1.key1 = T2.key1                   --one-to-one join
  INNER JOIN TABLE3 as T3 (nolock)
        ON T1.key1 = T3.key1                  --keys to T1.key1
       AND T2.key2 = T3.key2                --keys to T2.key2

```

Ugh...

And then there's the Cartesian join, which basically is a "no join".

```
SELECT *
FROM TABLE1 as T1 (nolock)
    TABLE2 as T2 (nolock)
```

With a Cartesian Join, for each record in Table1, all the records in Table2 are returned.  So, if T1 had 10 records, and T2 had 5 records, 50 records would return (10 x 5).  Folks hardly ever use this, but I have a case at work where I use such a thing to add a lot of things to a database based on new records that showed up in another query...something along this logic.

> For each new car that comes in the door, add all these things from the checklist template table to the master checklist table...doors, lights, oil, engine, etc.

That's not actually the case (I don't work for a car company), but that's the best way I can make the example make sense.


Anyways, you can handle the math either in the SQL statements, or in your code that's running the SQL statements.  Personally, I'd do it in the SQL statements, otherwise you'd have to run more queries.

EG: It's easier to just make a SQL statement that adds up Field1 + Field2 into Field3, then to make a query that pulls both those fields into a new table, run another query to add a column, run another query to add both the fields and dump their totals to the new column.  That's like 2 extra steps...what a pain.  

SQL is good for data manipulation and calculation, and Oracle SQL even has some good extra functions that MS SQL (Transact-SQL) doesn't have (like PAD function, which I sorely miss when working with Transact-SQL sometimes).

Google a good online SQL primer and read up on it.  SQL is a great thing to learn, because it's pretty easy once you get into it, and it's a pretty primary data manipulation language that can get assigned to string variables and ran in Data Access libraries.

---

### Post by SNYP40A1 on 2007-06-12
Tundro, I feel like I owe you a liver or something after that response :-).  Thanks for the help.  I see how I can replace the IF-statements and I actually already know how to JOIN tables as I am pulling data from multiple tables.  However, it seems like there are still two things missing:

1. Assume that I want to know the 80-th quantile door, window, and screen heights for all of these parts produced by my factory on a given day.  I want something that looks like this

[table]Day | Part | Height (80-th Quant) |
Monday | Door | 60 |
Monday | Window | 61 |
Monday | Screen | 40 |
Tuesday | Door | 61 |
Tuesday | Window | 59 |
Tuesday | Screen | 62[/table]

Humm...can't get the table function to work, but you get the idea.

2. Given the table above, I want to make a similar table, but it does not distinguish by part, so it would look something like this:

[table]Day | (ALL) Height (80-th Quant)
Monday | 60
Tuesday | 62[/table]

Now I want to map this table onto the first, so I would get another table that looks like this:

[table]Day | Part | Height (80-th Quant) | (ALL) Height (80-th Quant)
Monday | Door | 60 | 60 |
Monday | Window | 61 | 60 |
Monday | Screen | 40 | 60 |
Tuesday | Door | 61 | 62 |
Tuesday | Window | 59 | 62 |
Tuesday | Screen | 62 | 62 [/table]

So in the above example, each of the additional columns needs to be calculated based off of information contained in all the other rows.  So it's not like the new calculated columns are just based on one entry, in other words, I do not think that it is as easy as 

Select *, Area = height * width
From...<rest of SQL query>

And of course, once I have the table above, I would want to take one column and divide it by the other, for all entries.  So for these two reasons above, I still do not see how I can create queries that does the above.  recordset is a new concept for me.  I will read up on it.  Do you still think that it is possible to implement the above example in SQL alone without any post-processing provided by another programming language (in other words, execute SQL script from Perl and then calculate new table(s)?

---

### Post by Tundro Walker on 2007-06-13
Ok, the stuff you're trying to do would take either dumping out tables, like you said, or, since you're using Oracle, you should be able to make "Views".  Views are basically where you make a query, then turn it into a View, where-by it can be used as a table.

So, you make your query for step 1 into a View.  Then, you make a query that rolls up the avg (?) of all the heights for each day as a second query / view.  Then, you just have another query that joins both those views via day.

Or, just do like you were saying, have the 1st 2 queries make temp tables, which you then join on the Day column via a 3rd query (which can also be used to calculate the other values you were talking about dividing).  When you're done with the results, you can either dump them to a historical archive table for tracking, or dump out a report, whatever.  Then, just purge your temp tables at the end.

If you have MS Access at work, you can use pass-through queries to dump your SQL statements into Access and have it directly tap the SQL server your pinging (you would supply the DNS or whatever in the "properties" pop-up of the query).  By using a pass-through query, you bypass MS Access' slow query interpreter, and also bypass having to link in tables and crap.

When I do this kind of thing at my job with MS Access, I usually make 1 pass-through query to pull all the pertinent data I need.  Another "Make Table" query that's based off the 1st to basically pipe the data from the server into a table in my db.  Then, I have several queries that run off the main data.  If I was doing what you're talking about (having to take a rolled-up total and apply it to all records), I'd do like I said...make 1 query that pulled the records needed, another that rolled it all up with the avg (or whatever you're trying to get), then a third that joined the 2 queries.  Depending on how much data we're talking about, and how slow it would be pulling a result set from 2 joined queries, I may go so far as to have one or both of those middle-man queries dump their results into their own temp tables, then 3rd query joins off the temp tables.

As easy as MS Access makes, it does have it drawbacks.  It's not as powerful as slamming the server with SQL directly yourself (which I also have access to).  The good thing about MS Access is that you can use Task Scheduler to schedule and run macros.  So, once I have a chain of queries in place that gets the data I need, I chain them into a macro, and schedule the macro to run at 4am or what not.

I actually went so far as to make an MS Access database that does nothing but read in SQL statements, grind through them using the ADO (Active Data Objects), dump out the results as txt or Excel files, then email them to whomever they need to go.  I bet you could do the same thing with OpenOffice Base if you have the Python skills.  Afterall, they must have some kind of ADO-like library in Base to run recordsets and things.

---

### Post by SNYP40A1 on 2007-06-13
Tundro, thanks for your help.  I think that I have everything except for the median / quantile functions.  Ultimately, I want to spit out my results to an excel file.  I will read up on Active Data Objects, I have never heard of them before.  Do you know of a good forum to ask SQL questions besides here?  Like a place that is more focused on SQL specifically?

---

### Post by Tundro Walker on 2007-06-13
> **SNYP40A1 said:**
> Tundro, thanks for your help.  I think that I have everything except for the median / quantile functions.  Ultimately, I want to spit out my results to an excel file.  I will read up on Active Data Objects, I have never heard of them before.  Do you know of a good forum to ask SQL questions besides here?  Like a place that is more focused on SQL specifically?

Not really.  I just google things at work.  Google "SQL reference" and I'm sure you'll find a good reference that will not only help you with the SQL basics, but perhaps how to create the calculated median / quantile formulas, so you can do those as fields instead of running the data through a post-processing function.

ADO is a Microsoft thing.  It's a Visual Basic library that handles data connections, recordsets, etc.  Some VB.Net programmers use it when making applications that provide stand-alone data-tapping capabilities.  MS Access (from 97 on through 2003) has come with it as a main reference, since it uses a lot of its code library to handle data manipulation in the MS Access application.  I personally use the ADO library inside MS Access VBA (Visual Basic for Applications) IDE to help automate Access db's I make.  The great thing about that is you can link in a reference to Excel (since most computers with MS Access also have MS Excel as part of the whole MS Office suite.)  Then, you can do like I do, and automate MS Access to pull data, merge/convert/requery it until you get what you like, then have MS Access open MS Excel and dump the data to a spreadsheet, create pivot tables off it, etc.  A lot of folks scoff at that sort of stuff, saying "that's not real programming" or what not.  But, all I have to say is, I can take a computer that has MS Office on it, and do ALL my automation on it, where as other developers have to get special IDE's or code libraries or what not installed on their machines (some of which may have licensing issues, or cost tons of money to buy).  I'm the type of person that likes to work with what I've been given, so that's why I focused on MS Access & MS Excel for a lot of my reporting.  That, and the fact that everybody at my office has MS Office, so they can open and use the Excel reports I send out.  MS Access is a pretty good tool for what it can do.  It's just that it's sometimes buggy, and its built in query interpreter can be slow if you link in tables from other db's and build queries in the Access GUI to tap them.  That's why I prefer to use pass-through queries to pipe my SQL directly to the server I'm working with.  Depending on what you're querying, it can be up to 1000%+ faster than letting MS Access' query interpreter handle it.  However, one of the coolest things with MS Access is that it gives the "common" person (IE: someone with little technical ability) the power to link to tables from different DB systems (Oracle, SQL Server, other Access db's, Excel spreadsheets, CSV/TXT tab-delimited files, etc), and use those linked tables like regular tables inside MS Access.  So, I could hook in a table from Oracle and SQL Server, then create a query that joins them as if they were on the same server/DB.  Pretty cool.  MS Access is a very powerful tool, but sadly, most folks try to use MS Excel as their "data management" tool, because it's easier to use, and each cell can be any data type (and color, and font, etc).  I really hate getting other people's spreadsheets to work with, because while they usually look real pretty, they usually have very little data structure or require tons of scrubbing to turn into something finally usable inside MS Access.

Depending on the programming language you're going to use to automate stuff, you might want to google the programming language name, and " sql library" or something like that.  EG: "C SQL library".

---

### Post by SNYP40A1 on 2007-06-13
Tundro,
    Thanks again for your help.  It probably sounds like I am trying to lean away from having SQL do all the work in favor of avoiding post-processing.  The reason why I do post processing, in JMP currently, is because even the post-processing is automated in JMP.  It's just one big script that runs and at the end, I have all my data.  Where I die is when I have to manually copy cells from the JMP sheets that it produced into one Excel sheet.  This process eats up about 10-15 minutes of my week, which might not sound like much, but it's lost time that adds up.  I think the JMP syntax is concise and it was designed for someone without much programming experience to use.  However, it has a lot of weird quirks such as not executing some "Close" lines.  Like if I ask it to close a table and I execute the entire script, it often will not close the table.  But if I execute only everything up to and including the close command, the table closes.  But mainly, it's the whole copying and pasting thing that just gets too tedious.  Beyond that, JMP is expensive and closed-source.  It's a great piece of software for data analysis, but if there is an alternative that is open source and free, well, that's where I will prefer to invest my time in learning.  So anyway, main reason that I was leaning away from having SQL do most of the work is because sometimes I pull a lot of data, like 800,000+ rows of data.  I work at a company like AMD or Intel and gather die-level data from wafers processed each week.  I only look back over the previous few weeks and summarize the data in an excel sheet, which shows information by week.  Basically, I am making an indicator excel sheet for die test time so that we can track how long each die takes to sort as a function of test program, process maturity, and a lot of other variables.  So I am pulling a lot of data and using servers that others use as well.  If it is not any easier to post-process the data using some kick-*** programming language that is perfect for executing and performing functions on SQL data, then that's the setup.  I was thinking initially that Perl is what I would want to use, but I am surprised that there is not a language that is just made for this stuff, actually JMP is, but I wanted to find something that was more customizable and more robust.

---

### Post by slavik on 2007-06-14
NOTES: 'a' and 'b' are table names. Perl, PHP, and Python were first that came into my head, another alternative is Ruby.

1. Allows me to execute SQL queries.

Perl, Python, PHP

2. Create a new column to be appended to the result of the above SQL query and allow the column to be defined by a function. For example, the column might be a boolean or character assigned based on the results of the other column(s).

Perl, Python, PHP

3. Take 2 queries and join, matching by column name.

Do this within the SQL query (should be obvious) (sample: select * from a, b where a.name = b.name)

4. Allow for summary. Take the table from above and group by one column entry and for that group summarize other columns by median, mean, or quantile. For example, say I have one column called "Part" which is either a door, window, or stair. For all doors, I want to know the mean or median height. Same for all windows and stairs.

Do this within the SQL query, too. :) (sample(not sure if proper query): select *, average(a.height) from a GROUP BY a.type)

5. Eventually I will get a bunch of numbers from the above operation and I will want to make a composite table out of all the entries. For example, one cell in the composite table might be the median of height for all doors produced on a certain day (where cols would be by day).

seems like by this time, this is already done.

NOTE2: I suggest a good SQL book (I dunno what is good) :)

---

### Post by Tundro Walker on 2007-06-14
I'm curious if you can hook in libraries to JMP.  I'm not even sure what JMP is, but if it's anything like VB, Python, C, and all the other languages, there's got to be a way to hook to the Excel library, and then use the JMP code to execute instructions with it.

The folks that built MS Excel were actually pretty smart, and designed a function that pipes data from a recordset object right into a spread-sheet.  No need for doing your own arrays or what not.  I think the function is "CopyFromRecordset" or something.  Anyways, if you could link in the Excel library into JMP, you could

1) have JMP do the rudimentary SQL statements (just getting the raw data)
2) have JMP do the post-processing use whatever code you like to use in it
3) have JMP take your transformed data and "copyfromrecordset" into an excel spreadsheet.

Of course, that would entail that you dump your data into a recordset object, so I'm not sure what kind of SQL / Recordset / Data Connection library JMP uses, but it's gotta have something.  There's got to be a way to either do it already, or expand it with code libraries so you can do it.

As a side-note, you could try another thing...all Windows computers these days come with Windows Script Host.  This lets you run VBScript (.vbs) and JavaScript (.js) files on your computer as if they're executables.

All Windows comps should also have MDAC (Microsoft Data Access Components) loaded on, and I'm assuming you have MS Office.  So, you could use a Java Script or VB Script to tap into the MDAC / ADO libraries, create a recordset from your end-result data, and dump that right into Excel with the CopyFromRecordset function.

I guess your process would look something like this...

1) Do your rudimentary SQL tables stuff in JMP
2) Do your post-calculations in JMP
3) Have JMP finish it all in a compiled temp table you can use to dump to Excel
4) Use a Java/VB script to run in Windows, create an ADO.Recordset object off a SQL statement that pulls your dumpable table.  The script also creates an Excel Application instance, a workbook & spreadsheet object, then you use the worksheet.CopyFromRecordset function to dump the ADO.Recordset into the Excel file.  Script saves it some where and you're done.

Of course, having mentioned that, I usually avoid WinScript like the plague.  My personal experience with it has been annoying at best, but probably because I use VBScript (since I know VB).  VBScript is a really dumbed down version of VB, and I get annoyed at having to go back and forth between creating some code in the VBA IDE of MS Access (or Excel), toss (what I know works in VBA) into a .vbs file, click to run it, then get a very annoying error pop-up saying it doesn't like "Line XYZ".  This has been for stupid things, like when I wanted to use a Format function (which works in VBA) to format today's date to "yyyy_mm_dd", so I can add that to the end of a file name.  But, I try running that format function in VBScript...ERROR WILL ROBINSON!  Because VBScript doesn't have a format function (the way VBA has it, at least).  So, I have to make a function that can format the date the way I want into a string, and it's annoying.  Of course, I'm not using a text editor that recognizes VBScript syntax (MS Notepad FTW...or loss in this case).  I wish I had an IDE-like thing for VBSCript, where I could just click on the libraries I want to use, and then it would provide intellisense to let me know what functions/methods are available.  After using Linux and Bash Scripting for a bit, I'm really annoyed at how pieced-together Windows is, and how limited its coding/scripting ability is compared to BASH.  DOS batch files are really limited and archaic with their syntax, and Win Script files are supposed to alleviate that, but MS doesn't provide a good text editor to create them with.  Stupid.

Ok, enough ranting, I need to go to bed.  Hope this helps.  You'll probably end up looking into PERL, and realize you can get it to automate everything...SQL pulls through a recordset/connection library, Excel through its library and probably even JMP.

---

### Post by SNYP40A1 on 2007-06-14
slavik, thanks for your help, but I want to do 4 on 3, not the other way around, pretty sure that makes a big difference.

RE: 4, yes, I could do average like you propose, but what about median and quantile?  Oracle SQL no support.

Tundro, thanks again for your post, let me read it over tomorrow more thoroughly.  Checkout Notepad++, its just an editor and might help with Windows Scripting, it's got text highlighting, autoformatting and all the good stuff.  It's the one piece of software aside from some games that I really wish was available in Linux.  It probably will be before too long.

---

### Post by slavik on 2007-06-14
> **SNYP40A1 said:**
> slavik, thanks for your help, but I want to do 4 on 3, not the other way around, pretty sure that makes a big difference.

RE: 4, yes, I could do average like you propose, but what about median and quantile?  Oracle SQL no support.

Tundro, thanks again for your post, let me read it over tomorrow more thoroughly.  Checkout Notepad++, its just an editor and might help with Windows Scripting, it's got text highlighting, autoformatting and all the good stuff.  It's the one piece of software aside from some games that I really wish was available in Linux.  It probably will be before too long.
then yes, you have to do this yourself, or write some kind of library to add support for these things to be able to do that.

---

