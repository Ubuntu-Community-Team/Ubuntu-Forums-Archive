---
title: "What is the best equivalent of MS Access now in Ubuntu?"
date: 2012-04-03
forum: New to Ubuntu
---

### Post by swarup on 2012-04-03
I switched over from Windows to Ubuntu in 2007, and have been using Kexi as my replacement for MS Access since that time. But there have remained a number of problems with it, such as that once a table is made there is no facility for creating a new column, or for renaming a column, or for hiding a column. Additionally, I found that moving from my previous Ubuntu (9.04) to 11.10, I could not get Kexi to install properly or accept the databases which I had created in 9.04. My demands on a database program are not great; I just need a program that allows me to create tables and do very simple tasks with them. What have people found to work well in the new Ubuntu distributions?

---

### Post by Basher101 on 2012-04-03
i dont know anything equivalent, but just a suggestion - did you try installing office in wine?

regards

---

### Post by jerome1232 on 2012-04-03
[http://www.openoffice.org/product/base.html](http://www.openoffice.org/product/base.html)

???

---

### Post by bfmetcalf on 2012-04-03
I was going to suggest LibreOffice, but I haven't used the database part much yet.

---

### Post by swarup on 2012-04-03
> **jerome1232 said:**
> [http://www.openoffice.org/product/base.html](http://www.openoffice.org/product/base.html)

???

Actually, when I first switched over from Windows to Ubuntu in 2007, Base was the first thing I tried. I used it for the better part of a year, but found it to be very buggy, extremely complex, and difficult to use. At that time doing even the simplest of tasks in Base was lengthy and technical. Ultimately I moved everything over to Kexi, which I found to be far more user-friendly. Has base improved much since then?

---

### Post by winh8r on 2012-04-03
You will have LibreOffice Base installed by default in Ubuntu 11.10, does it not work for you?
(this is the replacement for OpenOffice Base in Ubuntu)
It is broadly compatible with M S Access.

---

### Post by swarup on 2012-04-03
> **bfmetcalf said:**
> I was going to suggest LibreOffice, but I haven't used the database part much yet.
 
Actually, I haven't put a new distribution on my laptop yet-- still use 9.04! So I haven't personally used LibreOffice, and didn't know it had a database application. Has anyone used it, and how have you found it to be? I'm looking for something straightforward, clear, simple to use.

---

### Post by jerome1232 on 2012-04-03
I actually haven't used it, I just figured Libreoffice being the MS office equivalent for Linux, would be closest your going to get.

I only briefly used access for a database class, then we used mySQL and SQL.

edit: Libreoffice is pretty much Openoffice with a different name on it.

---

### Post by swarup on 2012-04-03
> **winh8r said:**
> You will have LibreOffice Base installed by default in Ubuntu 11.10, does it not work for you?
(this is the replacement for OpenOffice Base in Ubuntu)
It is broadly compatible with M S Access.

As I say, I haven't put 11.10 on my own personal laptop yet, so haven't had the opportunity to try LibreOffice Base. Have you found it to work well? MS Access was just about the only thing I liked in windows, and I haven't been able to find a satisfactory replacement for it in all these years. i.e. a program which does what it is supposed to do, is clear and simple to use, and free of bugs.

---

### Post by Irihapeti on 2012-04-03
You can also use Base as a front-end to another database program. I use sqlite, along with the odbc drivers. I'm using OpenOffice.org rather than LibreOffice, but I don't think that would make much difference.

The structure of the database can't be edited directly in Base, it seems, but I use sqlite-manager extension in Firefox to do that.

I believe that there are also other sqlite editors in Ubuntu, and these may be enough for what you are wanting to do.

---

### Post by forrestcupp on 2012-04-03
LibreOffice Base is dismal. It absolutely cannot be considered a viable alternative to Access.

> **Basher101 said:**
> i dont know anything equivalent, but just a suggestion - did you try installing office in wine?

regards
MS Office works fine with Wine, but Access does not. It's impossible to get Access working with Wine. (And Publisher, too, for that matter)

I'm afraid that if you need something like Access, your best bet is either going to be to dual boot, or to create a Windows virtual machine and install it in the vm. VirtualBox is pretty good for this type of thing. You'll need to have a valid copy of Windows to do that, though.

---

### Post by swarup on 2012-04-03
> **Irihapeti said:**
> You can also use Base as a front-end to another database program. I use sqlite, along with the odbc drivers. I'm using OpenOffice.org rather than LibreOffice, but I don't think that would make much difference.

The structure of the database can't be edited directly in Base, it seems, but I use sqlite-manager extension in Firefox to do that.

I believe that there are also other sqlite editors in Ubuntu, and these may be enough for what you are wanting to do.

Irihapeti, is that you? From our lengthy discussions in the Puppy-linux forum years ago about setting up puppy in Hindi & other languages? How are you? I do remember that you were very involved with Database work at that time. Tell me, is Base easy to use? Bug-free? Better than it was in 2007?

---

### Post by swarup on 2012-04-03
> **forrestcupp said:**
> LibreOffice Base is dismal. It absolutely cannot be considered a viable alternative to Access.


MS Office works fine with Wine, but Access does not. It's impossible to get Access working with Wine. (And Publisher, too, for that matter)

I'm afraid that if you need something like Access, your best bet is either going to be to dual boot, or to create a Windows virtual machine and install it in the vm. VirtualBox is pretty good for this type of thing. You'll need to have a valid copy of Windows to do that, though.

This is indeed unfortunate news. Lack of a good database program has been the most frustrating aspect of my life in Ubuntu the past six years. Kexi has been the best thing I've used so far, and overall for my needs it has been good compared to my previous experience with OO Base. But due to the shortcomings noted in my first post, along with other problems, I am always on the lookout for something better.

I guess I could go back to MS Access, after all these years. It was really an excellent DB program. But that would require the short of arrangement you describe, which could surely be done-- I'd want to do it as Virtual Box if I did it at all. It is a bit sad to contemplate bringing Windows back into my laptop. Perhaps for this purpose though it is the best alternative...

---

### Post by lykwydchykyn on 2012-04-03
This is not exactly a desktop application, but you might check out wavemaker studio.  It's a web-based java app that allows you to build forms and connect them to just about any database engine you want (postgres, mysql, ms-sql, sqlite, etc).  It's graphical, much like the form builder in access.

It's not in the repositories, but it is free.  You download it from [http://www.wavemaker.com/](http://www.wavemaker.com/).

I haven't found a desktop tool that really approaches what Access does, even on Windows (Paradox used to be the big competitor, but it's kind of fizzled), but it doesn't sound like your needs are overwhelmingly complex.  Postgres has a nice desktop administration/configuration tool that can do some simple reporting and data entry called pgadmin3.  It's available in the repositories, as it postgres.

---

### Post by malspa on 2012-04-03
Access was the only reason I kept Windows here as long as I did. Then I ended up changing jobs and didn't need Access at home anymore. That was a few years back; sorry to hear that there's still no real replacement for it in Linux.

---

### Post by swarup on 2012-04-03
> **lykwydchykyn said:**
> This is not exactly a desktop application, but you might check out wavemaker studio.  It's a web-based java app that allows you to build forms and connect them to just about any database engine you want (postgres, mysql, ms-sql, sqlite, etc).  It's graphical, much like the form builder in access.

It's not in the repositories, but it is free.  You download it from [http://www.wavemaker.com/](http://www.wavemaker.com/).

I haven't found a desktop tool that really approaches what Access does, even on Windows (Paradox used to be the big competitor, but it's kind of fizzled), but it doesn't sound like your needs are overwhelmingly complex.  Postgres has a nice desktop administration/configuration tool that can do some simple reporting and data entry called pgadmin3.  It's available in the repositories, as it postgres.

Indeed, my needs are very simple. I don't even need to run queries! And I don't need forms for data entry either. I enter my data directly into the table. I just need to keep 7 or 8 tables to house the data for various works I am involved in. The tables can get quite large, with many columns, and I access the data straight from the table itself. So it is quite simple work. But the table needs to be sound, it should offer the flexibility of changing the names of columns as desired, adding columns later on, hiding columns, sorting alphabetically by any column. These sorts of simple functions. But I haven't found any DB application in Ubuntu that can do this well.

The first app you mentioned is web-based, which makes me feel a bit shy. I like to have my data in my computer. I'll have a look though. And the postgres app, is it simple? Sounds like a terminal-based app. I need it to be a GUI, and simple to use.

---

### Post by bfmetcalf on 2012-04-03
If you aren't using queries or forms or any of that.  Wouldn't an Excel type program work just as well?

---

### Post by swarup on 2012-04-03
> **bfmetcalf said:**
> If you aren't using queries or forms or any of that.  Wouldn't an Excel type program work just as well?

Perhaps I should consider this-- you mean a spreadsheet application, right? I've never used one in any serious way. Do spreadsheets work in just the same way as tables, with the same concept of columns and rows, with row id numbers etc, and ability to label the type of data which will be entered in each column i.e. text, date, etc? And can one sort by any column? And rename the columns later as needed? And add new columns later?

---

### Post by Irihapeti on 2012-04-03
The tables I use are relatively small: 20 to 30 records and about 15 to 20 columns, so sqlite is fine for that. I can't recall having any crashes or other unfortunate incidents with my setup. 

I don't know what the maximum size is for sqlite use. I think that if I were doing large tables, I'd set up something like MySQL or PostGreSQL instead, still using Base as a front end, because I like having a data entry screen.

Sure, nothing may be as good as Access, but the question here is whether the power of Access is in fact necessary, or whether something else is capable of doing what's needed.



Swarup, that's me. But I was working on Scim at the time - any database work was purely incidental.

---

### Post by swarup on 2012-04-03
Irihapeti, I only need around 15 to 20 columns myself in all likelihood. But the number of records can go to 2000 or more. Will sqlite be able to manage that many records? If it is clean and easy to use as a table format, with a clear GUI and the features I mentioned above-- ability to add columns, rename columns later, hide columns, increase font size and cell height. 

bfmetcalf was mentioning the possibility of using a spreadsheet for my purpose, so I opened OO calc just now to look at it. Can one name the columns? Or are they fixed with the names "A", "B", "C", "D" etc. If so, that would be a problem for me.

---

### Post by Vaphell on 2012-04-03
when all you know is a hammer then the whole world looks like a nail, huh? ;-)

letters for columns and numbers for rows identify cells and you can write formulas that take advantage of that addressing scheme
if you want to store data in named columns simply enter text in cells of 1st row and appropriate stuff below that header.

sqlite most certainly would handle your case, no problem. Firefox uses it for everything and works ;-) I have SQLite Manager addon for firefox installed and it allows for easy access and modification of sqlite files.

---

### Post by Mait on 2012-04-03
> **swarup said:**
> Irihapeti, I only need around 15 to 20 columns myself in all likelihood. But the number of records can go to 2000 or more. Will sqlite be able to manage that many records? If it is clean and easy to use as a table format, with a clear GUI and the features I mentioned above-- ability to add columns, rename columns later, hide columns, increase font size and cell height. 

bfmetcalf was mentioning the possibility of using a spreadsheet for my purpose, so I opened OO calc just now to look at it. Can one name the columns? Or are they fixed with the names "A", "B", "C", "D" etc. If so, that would be a problem for me.
> Perhaps I should consider this-- you mean a spreadsheet application, right? I've never used one in any serious way. Do spreadsheets work in just the same way as tables, with the same concept of columns and rows, with row id numbers etc, and ability to label the type of data which will be entered in each column i.e. text, date, etc? And can one sort by any column? And rename the columns later as needed? And add new columns later? 
I don't think you need Access or whatever 'relational' database management tool. Calc - spreadsheet much better for you.

You could write any column name at very first row then put records below. Add column, change colmn name whatever you want. Need new table? use just another sheet. Sort, date, text, etc all are there. You can change look and feel very easy. 'Spreadsheet' is what for you said.

Hope you enjoy Excel or Calc.

---

### Post by swarup on 2012-04-03
Oops-- I was waiting for replies and hadn't noticed that replies had started on this third page!

Thank you Vaphell and Mait-- I'll look at sqlite and will seriously consider the possibility of opting for a spreadsheet like Calc. I think you may be right, that I've been waiting for a good DB program all these years, when a spreadsheet program would also work fine...

---

### Post by swarup on 2012-04-03
I've just exported one of my tables from Kexi and imported it into Calc, to see how it looks and how I can work with it in spreadsheet format. I tried sorting one of the columns alphabetically, and was shocked to see that it sorted that column only, and left all the rest of the data as it was. The spread sheet does not seem to treat all the data in one row as a record, as a single linked group of data. I need to be able to sort one column alphabetically, and have all the data in each record (each id#), stay linked. Is there a simple way to sort this way using Calc or any common spreadsheet app?

---

### Post by bfmetcalf on 2012-04-03
You need to highlight the entire sheet to get it to sort like you want, but it should do it just fine.

---

### Post by Irihapeti on 2012-04-03
You can use the "data" menu to define the range you've selected and give it a name, and then to select the range later when you want to sort.

---

### Post by lykwydchykyn on 2012-04-03
> **swarup said:**
> 
The first app you mentioned is web-based, which makes me feel a bit shy. I like to have my data in my computer. I'll have a look though. And the postgres app, is it simple? Sounds like a terminal-based app. I need it to be a GUI, and simple to use.

Just because it's web based doesn't mean the data isn't on your computer.  It just mean the browser is your interface.  When you install it, it sets up tomcat on your machine and serves itself locally.  The database server can also be located locally.  But all that seems moot since you don't need forms.

pgadmin3 is not a terminal app, as I said it's a graphical application.  You can see a screenshot of it here:

[http://screenshots.debian.net/screenshots/p/pgadmin3/18_large.png](http://screenshots.debian.net/screenshots/p/pgadmin3/18_large.png)

You might also look at sqlitebrowser, a GUI front-end for sqlite.  It's probably simpler to work with than pgadmin3.

EDIT: reading these other posts, I think everyone is on to something with the spreadsheet.  If you aren't even querying the data, it makes no sense to mess with a relational database.

---

### Post by mastablasta on 2012-04-04
> **lykwydchykyn said:**
>  
You might also look at sqlitebrowser, a GUI front-end for sqlite. It's probably simpler to work with than pgadmin3.
 

 
just to add here a bit (in case relational databse is still something OP would want to do) that sqlite has a number of GUI interfaces available. soem are not so good while other have almost everyhting doen via a nice user friendly GUI interface.

---

### Post by swarup on 2012-04-04
I have been playing with Calc this morning, but I cannot get it to sort the way I want. Let's say I want to sort alphabetically z->a according to the third column. If I highlight just the third column, then the sort command sorts just that column (which is quite scary-- de-linking all my data). And if I highlight the whole spreadsheet and click sort z->a, then it sorts according to the first column, as it appears by default or something. 

And in the process of doing multiple sort procedures and undoing them, the first row (containing my column names) somehow got allotted to the bottom of the spreadsheet, so I could not longer see the column names at the top. Not only that-- even if everything is sitting properly in the spreadsheet, if you merely scroll down the table, then the first row containing the column names obviously is no longer visible on the screen. 

It seems to me that a spreadsheet is really not made to house a table-- even for the very simple reason that the column names are stuck ad hoc in the first row, and that first row is not always going to be visible.

But for now I will be willing to test this spreadsheet arrangement, if I can get the sort command to work as I need. How can I, say, sort z->a with the 4th row, and have all the records remain intact? 

(Irihapeti, I do not know where the "data" menu is-- but even if I find it, it sounds like it might be a bit complex for a sort procedure-- especially when I will need to be constantly doing sorts, and by various columns, all day long.)

---

### Post by forrestcupp on 2012-04-04
> **swarup said:**
> I have been playing with Calc this morning, but I cannot get it to sort the way I want. Let's say I want to sort alphabetically z->a according to the third column. If I highlight just the third column, then the sort command sorts just that column (which is quite scary-- de-linking all my data).Have you checked to make sure it is actually de-linking your data? Usually when you have it move things around, it is pretty smart about moving the links, too.

> **swarup said:**
> Not only that-- even if everything is sitting properly in the spreadsheet, if you merely scroll down the table, then the first row containing the column names obviously is no longer visible on the screen. This can easily be fixed. Just use the first row for your header column names. Now select the row directly under that row, and click "Freeze" in your "Windows" menu. Now you can scroll everything else, and your header row will be frozen in place.

But still, if you can't get it all figured out, a spreadsheet may not be what you're looking for. I'm sure there are ways to do everything you need to do in Calc, but it's all going to be a lot of manual work.

---

### Post by swarup on 2012-04-04
> **forrestcupp said:**
> Have you checked to make sure it is actually de-linking your data? Usually when you have it move things around, it is pretty smart about moving the links, too.

Well, if it is not de-linking the data then someone would have to teach me about how it is not de-linked. Because once I start sorting individual columns independent of the rest of the table, it looks pretty outrageously de-linked to me. 

> **forrestcupp said:**
> This can easily be fixed. Just use the first row for your header column names. Now select the row directly under that row, and click "Freeze" in your "Windows" menu. Now you can scroll everything else, and your header row will be frozen in place.

Wow! That is an amazing feature. This is a big breakthrough for me, very helpful. 

Now I would just need to have the sorting procedure made clear i.e. how to sort and keep all the records intact.

> **forrestcupp said:**
> But still, if you can't get it all figured out, a spreadsheet may not be what you're looking for. I'm sure there are ways to do everything you need to do in Calc, but it's all going to be a lot of manual work.

I don't think Ubuntu has what I am looking for-- that is, a simple, smooth-working replacement for MS Access. But in the absence of that, I am starting to wonder whether a spreadsheet may be the best alternative for me.

---

### Post by JKyleOKC on 2012-04-04
As a long-time user of Windows (going back to Win3.1 days) and also Linux (since Slackware 2.0), I don't think I would ever characterize MS Access as "simple and smooth-working." It does, however, do its intended job well enough to be useful.

In Linux, I've found MySQL to be its best equivalent although it's not a direct replacement since MySQL does not deal with *.MDB files. If you're comfortable with the SQL view when using Access, you'll be quite at home with MySQL -- and you can export the data from Access and import it into MySQL via CSV-formatted files.

For a quick and dirty database in Linux, however, I'll second the use of a spreadsheet, and recommend "gnumeric" rather than Base as the one to use. It's an almost total clone of MX Excel, is quite easy to work with, and in my Xubuntu system came installed by default. When I go to data->sort in gnumeric, it lists columns and provides for removing those you don't want to use in the sort keys, and rearranging their position in the keys without moving them in the file itself. All in all quite good for small data sets...

---

### Post by SeijiSensei on 2012-04-04
Just a few comments....

MS Access is the reason why I have a VirtualBox VM running Win7 on my Ubuntu machine.  Unlike the OP, I use relational databases and often need to query a set of three or four joined tables.  The databases reside in PostgreSQL on a remote server (hundreds of miles away, in fact) to which I connect with [ODBC]("http://en.wikipedia.org/wiki/ODBC").  

I know how to write SQL queries and can accomplish the same tasks with the command-line client, but it's often easier to use Access when the query gets complex with multiple joins and multiple selection criteria using fields residing in different tables.

There is nothing in the Linux world that I've found that can touch Access for tasks like these.  It's also trivially easy to create and update tables in Access by importing the data from a spreadsheet.  Importing data from an HTML table is also quite simple:  highlight the data on the web page and choose copy in the browser, paste into Excel. then import the table via Access.

That said, I endorse the spreadsheet approach for the types of tasks the OP has described.  A couple of the problems you've mentioned can be easily resolved.  First, all the spreadsheets I've used let you designate the top row of a table as a set of field names.  To sort all the data by one or more columns, just highlight all the data, including the field names, and choose Data > Sort.  Check the box that tells the spreadsheet to treat the top row as names.  You should then be able to designate the sort columns and directions.

Another alternative, though a more complex one, is to install the [LAMP]("https://help.ubuntu.com/community/ApacheMySQLPHP") stack on your machine which gives you the Apache web server, the PHP scripting language, and a copy of MySQL.  You can then install a program called [phpmyadmin]("https://help.ubuntu.com/community/phpMyAdmin") which lets you manage the data with a web browser.  It only makes sense to do this if you're actually running SQL queries or the data have a relational structure.  For simple data management tasks you're better off using a spreadsheet.

---

### Post by swarup on 2012-04-04
What about let's say I've got 20 columns in a table. Take the following few scenarios:

1. One of the columns is a date column, and I want to select all the records containing the year 1920, and just show those. Will a spreadsheet allow me to do that? Or do I need a DB to run a query for this sort of thing?

2. I want to hide 14 of the columns, and just work for a few hours with 6 of the columns.

3. I want to rearrange the order of the columns, moving some of them to the left of the page next to each other, and others to the right.

Can the above three tasks be done using a spreadsheet, or do I need a database program for it?

---

### Post by SeijiSensei on 2012-04-04
> **swarup said:**
> 1. One of the columns is a date column, and I want to select all the records containing the year 1920, and just show those. Will a spreadsheet allow me to do that? Or do I need a DB to run a query for this sort of thing?

Depends on how fancy the output needs to be.  You can always just sort on the date column then scroll down to the records with 1920 in that field.  If you want a more complex solution, there are functions that let you select rows according to a criterion.

> 2. I want to hide 14 of the columns, and just work for a few hours with 6 of the columns.

Select the columns to hide and choose Hide Columns.  All spreadsheets have this feature, often available by right-clicking on the selection.

> 3. I want to rearrange the order of the columns, moving some of them to the left of the page next to each other, and others to the right.

Use cut and paste.  You may need to insert some empty columns next to the destination column before pasting.

---

### Post by forrestcupp on 2012-04-04
> **swarup said:**
> Well, if it is not de-linking the data then someone would have to teach me about how it is not de-linked. Because once I start sorting individual columns independent of the rest of the table, it looks pretty outrageously de-linked to me. I think you're going to have to give us a simple, but real world example of what you are trying to do, and how things are linked together. There's no way we can help you if you don't.


> **swarup said:**
> Wow! That is an amazing feature. This is a big breakthrough for me, very helpful.Freezing rows is very useful. Another thing that might come in handy for you is grouping rows or columns. You can select any number of adjacent rows or columns and go to **Data->Group and Outline->Group** and it will group the rows/columns together to where all of the ones in the group can be hidden or shown by clicking the + or - icon. Note that the entire row or column will be grouped. It's not possible to only group certain cells.

---

### Post by swarup on 2012-04-04
forrestcupp, I've got the sort worked out now-- thanks. Although the a-z sort seems to only work with only column, but the data -> sort works very well and keeps the data linked-- both in Calc and in Gnumeric.

Many thanks to you both, SeijiSensei and forrestcupp; I will try out your suggestions and see what works best. But it looks like a spreadsheet application may well fit my needs most.

---

### Post by Mait on 2012-04-04
Although I suggested spreadsheet, now looks like this tool is better for your situation. Check out this screencast.
[http://www.youtube.com/watch?v=A2E-cjUcLRw](http://www.youtube.com/watch?v=A2E-cjUcLRw)

It's firefox addon, you can install it here,
[https://addons.mozilla.org/en-US/firefox/addon/sqlite-manager/](https://addons.mozilla.org/en-US/firefox/addon/sqlite-manager/)

Ubuntu provides some sqlite management tool like sqliteman and sqlitebrowser, but this addon is better for browsing. (I've tried two tools.) If you could learn some sql select query, it would be more powerful tool for db browsing.

[http://www.w3schools.com/sql/sql_select.asp](http://www.w3schools.com/sql/sql_select.asp)

(Actually I've learned some query for screencast at there)

---

### Post by Irihapeti on 2012-04-04
Just for interest, here are the size limitations for SQLite: [http://www.sqlite.org/limits.html](http://www.sqlite.org/limits.html)

I doubt very much that you'd get anywhere near those with what you are doing.

---

### Post by cmcanulty on 2012-04-04
sounds like libre office calc would work fine for you would have to learn the interface but it's pretty easy

---

### Post by swarup on 2012-04-04
> **Mait said:**
> Although I suggested spreadsheet, now looks like this tool is better for your situation. Check out this screencast.
[http://www.youtube.com/watch?v=A2E-cjUcLRw](http://www.youtube.com/watch?v=A2E-cjUcLRw)

It's firefox addon, you can install it here,
[https://addons.mozilla.org/en-US/firefox/addon/sqlite-manager/](https://addons.mozilla.org/en-US/firefox/addon/sqlite-manager/)

Ubuntu provides some sqlite management tool like sqliteman and sqlitebrowser, but this addon is better for browsing. (I've tried two tools.) If you could learn some sql select query, it would be more powerful tool for db browsing.

[http://www.w3schools.com/sql/sql_select.asp](http://www.w3schools.com/sql/sql_select.asp)

(Actually I've learned some query for screencast at there)

Wow, thanks for doing all that-- very interesting, I'll definitely try it out. And Irihapeti, thanks for letting me know the size limitations-- I see it won't be a problem.

---

### Post by cmcanulty on 2012-04-04
did you try glom

---

### Post by swarup on 2012-04-05
> **cmcanulty said:**
> did you try glom

Wow, so many options out there! I've just looked at their description and screenshots-- it looks very nice. But have you used it? There are many DB programs that have a pretty face i.e. look good from the outside, but when you start using them you find that they don't work like they are supposed to. It will be difficult for me to test them all, so that is why I ask: have you used glom, and (1) is it simple for the non-geek i.e. straightforward GUI (2) does it do what it is supposed to do and have reasonable features for managing a table as I have mentioned on this thread (i.e. ability to add new columns later; ability to change the names of columns later; ability to move columns; ability to hide columns; maintain the users set column width for each column from one session to the next)?

---

### Post by cmcanulty on 2012-04-05
i haven't used it but download all and try won't hurt and free the real beauty of linux

---

### Post by swarup on 2012-04-05
> **cmcanulty said:**
> i haven't used it but download all and try won't hurt and free the real beauty of linux

That's true. But the caveat is that, unlike in Windows where to install all you have to do is click on the .exe file and bing it's installed, not uncommonly in Linux for me it can be a real struggle to get something installed if it is not installable by Synaptic or Add/Remove (or the new software center). Otherwise, sure, I'd just install it all and have a look. But sometimes it involves funny manipulations or terminal commands to install, sometimes it involves compiling. So therein lies the complexity behind your suggestion...

---

### Post by forrestcupp on 2012-04-05
> **swarup said:**
> forrestcupp, I've got the sort worked out now-- thanks. Although the a-z sort seems to only work with only column, but the data -> sort works very well and keeps the data linked-- both in Calc and in Gnumeric.

I'm glad you got the sort worked out. When I was saying that the links should still be intact, I guess I just assumed you were using data->sort. :)

---

