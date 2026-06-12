---
title: "Database = overkill ?"
date: 2007-12-11
forum: Programming Talk
---

### Post by clash on 2007-12-11
Hey all

Starting development of an application which is going to record, edit, store some info. 

Basically a sports club management system, keep details of the club, members, teams, maybe some finance, equipment etc etc. 

I was just wondering what would be the best way to store this info ? 

I'm talking about a club having a max membership of say 100 people at most and just recording contact details etc for them. 

Is a database overkill here ? Would it be more of an idea to use XML or even a good old fashioned text file to hold the info ? 

At most and off the top of my head (i'm in really early planning stages here) I'd think if I went the databse route I'd need a table for members, table for equipment, table for teams (some members will be on more or less then one team), and just maybe some financial details. Club funding and what not. 

I personally would be of the mentality to just throw everything into text files but ..then again I'm a messy guy and haven't really developed anything like this before except for projects in University. 

I also would be hopeful that this software will everytually reach the stage where a number of clubs might use it so I want to do it "the right way". 

Thanks guys.

---

### Post by Compyx on 2007-12-11
For such a project I'd use Python and SQLite. SQLite is a light-weight yet powerful SQL 92-based database which just provides a library to work with a database, no server, no client.

And Python has an excellent interface: sqlite3. Combined with Python's easy of use and built-in GUI-support, you should be up and running in n no time.

You could also look into Python's libraries for XML-parsing or libraries such as shelve or pickle.

---

### Post by wieman01 on 2007-12-11
+1 in favor of a database. You never know where this project is going, so you might end up with a much greater number of users than initially perceived.

I recommend either MySQL or PostgreSQL. Both are very light too and easy to administer. 

A file-based data storage system is a no go, don't do it.

---

### Post by LaRoza on 2007-12-11
If you are sure it is going to be small forever, Python and SQLite are the way to go. Otherwise, use MySQL or another database server.

---

### Post by pmasiar on 2007-12-11
Start with SQLite, you can switch to real SQL database server anytime later.
Will it be single user desktop app, or multiuser LAN app? If multiuser, consider web app. 
Even if you don't use web app frontend, consider using ORM, will make data access even simpler.
If you go with Python (which I highly recommend), Django autogenerates basic DB admin stuff for you. Go for rapid app development, DB access will soak most of your speed anyway. If you don't know Python (or Ruby), this is the project to try it.

---

### Post by thornmastr on 2007-12-11
If this is for just one specific club and that club is using a Linux OS, everyone has offered some really good advise. However, if there are other clubs that might want to look at your package, the first question you need to consider is will it run  on MS and more importantly is will it run well on MS. Probably the answer to at least one or even both will be NO. Therefore first consider your possible platform. 

If you are dealing with MS, keep in mind MS Visual C++ and MS ACCESS as your database. My preference is always to code under UBUNTU. Unfortunately, paying my bills means most of what I do is under the MS umbrella. 

Just my 0.02 cents worth.

Robert

---

### Post by DavidBell on 2007-12-11
Make your life easy, and just do it in OOo Calc spreadsheet, one sheet per table. It has some database features if you need them later, or at least it will be easy to transfer data.

DB

---

### Post by aks44 on 2007-12-11
Definitely +1 for SQLite. It's very lightweight, yet powerful enough for most common tasks.

I guess Python may be a good choice too, it is renowned to be quite easy to use.

---

### Post by pmasiar on 2007-12-11
> **thornmastr said:**
> will it run well on MS. ... If you are dealing with MS, keep in mind MS Visual C++ and MS ACCESS as your database.

I am not sure what OS is MS -- you mean Windows I guess?

But... if OP wants cross-platform solution, will MS Access run on Linux? Thought so :-)

Both Python and SQLite **do** run on both Windows and Linux, so Python/SQLite fits your own criteria better than your solution :-)

---

### Post by LaRoza on 2007-12-11
> **thornmastr said:**
> If this is for just one specific club and that club is using a Linux OS, everyone has offered some really good advise. However, if there are other clubs that might want to look at your package, the first question you need to consider is will it run  on MS and more importantly is will it run well on MS. Probably the answer to at least one or even both will be NO. Therefore first consider your possible platform. 

If you are dealing with MS, keep in mind MS Visual C++ and MS ACCESS as your database. My preference is always to code under UBUNTU. Unfortunately, paying my bills means most of what I do is under the MS umbrella. 

Python and SQLite work on Windows and Linux very well. Why forsake a suitable cross platform solution, and offer restricted, less suitable alternatives?

---

### Post by metromari on 2007-12-11
You know your needs better than I, so my only suggestion is that "database" != "SQL". A database can be XML, "plain text", DBM, spreadsheet...

For what you are doing I wouldn't go anywhere near SQL. If I were doing this in Python, for example, I would put the information in Python data types (e.g. dictionaries) and then just use cPickle to store them. Or you can use shelve.

If you don't have a ton of data just do it in delimited text files and then process it using Awk or Perl or even Python.

A database is any data that's in structured form so you can do something useful with it. Often SQL is just overkill.

---

### Post by LaRoza on 2007-12-11
> **metromari said:**
> You know your needs better than I, so my only suggestion is that "database" != "SQL". A database can be XML, "plain text", DBM, spreadsheet...

For what you are doing I wouldn't go anywhere near SQL. If I were doing this in Python, for example, I would put the information in Python data types (e.g. dictionaries) and then just use cPickle to store them. Or you can use shelve.

A database is any data that's in structured form so you can do something useful with it. Often SQL is just overkill.

For this, using a database makes sense. It looks like it may grow, and looks like it could (should) have a web interface, so using Python/PHP with SQLite/MySQL is the best solution. With Python, it work work on any platform, and with SQLite, it will work just as well as a server side program or an application.

---

### Post by pmasiar on 2007-12-11
> **metromari said:**
> "database" != "SQL". A database can be XML, "plain text", DBM, spreadsheet...

While I agree that there are non-SQL databases, and you can store simple data in plain text, IMHO search/update and scaling issues are pretty important. 

XML, plain text, spreadsheet do not scale well, and query/update capabilities are nill.

> For what you are doing I wouldn't go anywhere near SQL. ... dictionaries...shelve.

and then you suggest to write custom search in fields, and custom update/save changes, inventing custom mini-language? How it is simpler than using standard and debugged SQLite?

> A database is any data that's in structured form so you can do something useful with it. Often SQL is just overkill.

My definition of [http://en.wikipedia.org/wiki/Database](http://en.wikipedia.org/wiki/Database) includes schema and query capabilities. Text file is NOT a database, it might be "data storage" or "repository" but not database. Especially XML is NOT simpler than SQL, but harder to use and harder to query.

You probably wanted to warn against using database server?

SQLite is exactly the kind of repository which is simple (does not require SQL server running) but scales well.

SQL database server  is overkill if your data can be stored in one or couple dictionaries, and always accessed via keys only. Other than that, SQLite is exactly the decent compromise between functionality, scalability and simplicity. No server (just a library accessing single datafile) with all the power of SQL query and schema.

Of course I have no idea what exact DB needs are, but it does not look like 2 dicts will cover it, and SQL scales up.

---

### Post by slavik on 2007-12-11
what's wrong with OOo Base for such a project? (MS Access equivalent), it can use a real database in the backend (MySQL, PostgreSQL) or a built in database.

Look ma, no need to write useless code. :)

---

### Post by metromari on 2007-12-11
> **pmasiar said:**
> 
XML, plain text, spreadsheet do not scale well, and query/update capabilities are nill.

My definition of [http://en.wikipedia.org/wiki/Database](http://en.wikipedia.org/wiki/Database) includes schema and query capabilities. Text file is NOT a database, it might be "data storage" or "repository" but not database. Especially XML is NOT simpler than SQL, but harder to use and harder to query.


Schema: colons as delimiters. Query: grep and awk. Update: echo new data >> textfile. That's hardly nil.

> 
SQL database server  is overkill if your data can be stored in one or couple dictionaries, and always accessed via keys only. Other than that, SQLite is exactly the decent compromise between functionality, scalability and simplicity. No server (just a library accessing single datafile) with all the power of SQL query and schema.


It also rips the user from the shell and all the useful utilities that have already been written for it, and encourages the programmer to build a UI from scratch even though the shell already has a UI with line editing, history, etc. 

Plain text databases: see

[http://www.rdb.com/](http://www.rdb.com/)

I'm not trying to say he shouldn't use SQLite; I'm just trying to say there are options other than SQLite and OO base.

---

### Post by pmasiar on 2007-12-12
> **metromari said:**
> echo new data >> textfile. 

That would be append, not update :-P  You just proved that OP would have to invent simple custom DSL to handle functions what SQL already does.

> It also rips the user from the shell and all the useful utilities that have already been written for it, 

It depends if OP is already expert in all those utilities, or better decides to future-proof the learning and learn SQL, which OP will need later anyway.

> and encourages the programmer to build a UI from scratch .

This is exactly NOT what I proposed, but your proposal forces OP to do: I suggested using SQLite, SQL was invented long time ago, just use it, and any SQL helper tool around it.

---

