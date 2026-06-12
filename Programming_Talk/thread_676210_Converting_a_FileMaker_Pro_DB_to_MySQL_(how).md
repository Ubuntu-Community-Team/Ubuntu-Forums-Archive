---
title: "Converting a FileMaker Pro DB to MySQL (how?)"
date: 2008-01-23
forum: Programming Talk
---

### Post by altonbr on 2008-01-23
I have a web development client that has a database in FileMaker Pro that she uses for her annual publication, but now her competitor has released a very similar database online that is fully searchable. Naturally, this lady wants this feature on her website as well, which I can help her do, but right now, her DB is locked up in a proprietary DB format.

One solution is to do this manually via data (re)entry.

I've found two conversion 'solutions' to this problem, but neither are open source and both seem to require Windows or a Mac.

[http://dev.mysql.com/tech-resources/articles/filemaker_mysql_whitepaper/filemaker_to_mysql_whitepaper01.htm](http://dev.mysql.com/tech-resources/articles/filemaker_mysql_whitepaper/filemaker_to_mysql_whitepaper01.htm)
[http://www.lassosoft.com/Support/FAQs/index.lasso?7460](http://www.lassosoft.com/Support/FAQs/index.lasso?7460)

The first looks like a great resource to look through -- and I am -- but after scanning, I get the general impression that I will have to purchase a piece of software called FMProMigration. The perl scripts it speaks of assist FMProMigration instead of acting as a separate entity.

So my question is: does anyone know of a pure Perl/PHP/Python (even ASP) method of converting between these two databases (.fp7 to .sql)?

I also read that FileMaker Pro 9 has support for using a SQL DB, but I'm unsure of it's conversion process or if it even has one...

---

### Post by cmnorton on 2008-01-24
1) Will file maker pro export to anything, like an Excel spreadsheet? 

2) Are there any db utilities for file maker pro?

3) Can you read the filemaker pro db using an ODBC link from Access or Excel? Can you read the db from Linux using ODBC on Linux?

You might consider your goal to be extracting the data from the file maker pro database by something that can read it. From there, you would get the data into delimited format. MySQL will read just about anything. It's quite good that way.

I don't have a copy of file maker pro, or I'd have gone off and researched this for you.

---

### Post by altonbr on 2008-01-25
> **cmnorton said:**
> 1) Will file maker pro export to anything, like an Excel spreadsheet? 

2) Are there any db utilities for file maker pro?

3) Can you read the filemaker pro db using an ODBC link from Access or Excel? Can you read the db from Linux using ODBC on Linux?

You might consider your goal to be extracting the data from the file maker pro database by something that can read it. From there, you would get the data into delimited format. MySQL will read just about anything. It's quite good that way.

I don't have a copy of file maker pro, or I'd have gone off and researched this for you.

Yeah, neither do I. I'll have to take a look at my clients computer in the up-coming weeks and try it out. Thanks for your input! I'll let you know how it goes.

---

### Post by cmnorton on 2008-01-25
Between free or cheap SQL clients out there, and stuff on File Maker Pro's Web Site, you should be able to extract the tables. You can even download an evaluation of File Maker Pro for testing.

Getting the extracted data loaded into MySQL is, as they say, academic (almost).

[http://www.filemaker.com/products/fms/index.html](http://www.filemaker.com/products/fms/index.html)
[http://www.filemaker.com/support/technologies/sql.html](http://www.filemaker.com/support/technologies/sql.html)

---

### Post by growlf on 2009-01-22
I realize that this thread is a bit old and may be dead - but I am both hopeful and curious.  Was there any solution to thi issue found?  ..any specifics.   I have a client that has an FP7 database of their store stock data and needs to convert it to MySQL or SQLite for Django access on their new Ubuntu setup (they have completely replaced their Windows OS with it :) ).  

Problem is, the old program does not have _ANY_ export feature that I can find beyond the backup to a proprietary format.  Any help is greatly appreciated.

---

### Post by dsimpson_dcsi on 2011-07-10
Readers of this post may be interested to know that the FmPro Migrator tool described in the MySQL white-paper link has been updated quite a bit over the last 8 years.

FmPro Migrator Platinum Edition now has the capability of converting not only the data, but also the graphical interface of the FileMaker database (Layouts, value lists, portals, vector graphics objects) into a PHP web application.

[Automated Layout to PHP Conversion]("http://www.fmpromigrator.com/services/php_conversion.html")

A few other things I can think of in regards to the data transfer:
There are a number of ways to export data at no cost from a FileMaker database file. All of these features are listed in the File -> Export Records... menu option.

But you need to be careful when exporting records this way. I have experienced problems exporting large data sets in this manner. Also the built-in export features won't export repeating fields into a usable format, and will not export image data from container fields. Repeating fields data receive extra processing, in order to convert them into a relational database structure - a table of records which are related to the parent table.

These limitations required me to write the FmPro Migrator tool in the first place. Whenever I transfer data from FileMaker databases, I always use an ODBC connection to read the data accurately so that I get every byte of data. For instance, some spreadsheet formats have been know to truncate data at 255 bytes per cell - so you don't want to experience hidden data truncation in this manner. 

If all you want to do is transfer the data, and you don't need to convert the graphical interface, there is a less expensive version of the product available for this task.

David Simpson
[www.fmpromigrator.com]("http://www.fmpromigrator.com")

---

