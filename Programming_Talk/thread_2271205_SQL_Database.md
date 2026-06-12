---
title: "SQL Database"
date: 2015-03-28
forum: Programming Talk
---

### Post by Matthew_Harrop on 2015-03-28
I'm currently working on a project to create an add-in to Microsoft Excel and I'm having a little trouble understanding where to put my database file.

I want to use a db file to hold important information, and hide the clutter, so that every time a user wants to use the add in, they don't need to launch the same spreadsheet.

 However, how do I specify where to create the db file when the add-in script is initially run?

---

### Post by ian-weisser on 2015-03-28
Is the db single-user or multi-user?
Is the db wiped at each logout/reboot? Or is it persistent?
Is the add-in Linux-specific? Or does it need to run on Windows and/or OSX too?

---

### Post by Matthew_Harrop on 2015-03-28
At this moment in time it will be single user, but I intend to allow the program to work with a single hosted database with multiple connections (IE 1 database, many spreadsheets)
It should be persistent, I don't want the user to have to re enter all their details every time they restart the computer
The Add-in is of Office so I'm not sure what the answer would be, however I am assuming Windows specific at this stage.

---

### Post by SeijiSensei on 2015-03-28
Is there are reason you've chosen not to use MS Access as the database?  It's designed to work with Excel.

---

### Post by ofnuts on 2015-03-28
I have worked with such a spreadsheet with a DB access in it, but I never really understood what the original author did to make it work. What I remember however was that the result was a real PITA to maintain, and that the target users (mostly developers!) were not always able to make it work because it required a DB configuration on every workstation (Oracle TNSNAMES). An Excel expert could answer this kind of question but I doubt you'll find such a person in a Linux forum.

---

### Post by SeijiSensei on 2015-03-28
All Office programs know how to make ODBC connections to back-end SQL databases.  I sometimes use Access as a client to a PostgreSQL database residing on a remote server.  Having worked with an Oracle back-end in the past, I would never choose that option unless presented with a fait accompli.  Both PostgreSQL and MySQL have ODBC connectors available that let programs like Access and Excel query the database directly.

However I can't tell from the OP's query if that is what he is trying to design.  It sounds more like he wants a self-contained application, not one that depends on a shared remote database.  That's why I suggested Access.  If its simply a matter of designing a query engine in Excel that uses a remote database, I'd go with an ODBC-based solution and PostgreSQL on the back end.

---

### Post by Matthew_Harrop on 2015-03-28
First, thank you for your responses! 
Second, The application is a rather strange one (I've never developed an add-in for another application before) Usually I would design a system that relies on a pre-built database by the installer (or the application builds it itself - Is that possible with office add-ins?) however I am rather unsure about how an office add-in is installed. When I deployed it (Just to see) it ran a script and seemed to work, however that was on my development machine...

I didn't want to use Access just in case any of my customers don't have access to Access ( :P ) I wanted to be able to do it in such a way as either the first thing the add-in does is check for the dB file and then either makes it and reads from it or just reads from it. Further I wanted to leave the window open to allow the add-in to connect to a central repository that contains info many users can use.

Perhaps its just a case of that being part of the deployment; A database has to be installed and configured (Either locally or on a remote) before the add-in can be used.

---

### Post by SeijiSensei on 2015-03-28
You keep talking about a "DB file."  What do you mean by that?  Something like Berkeley db with key-value pairs or maybe SQLite like Mozilla uses? I'm still pretty much clueless as to what you are trying to accomplish.

I don't think Office has any ability to interact with something like Berkeley db or even SQLite.  Microsoft presumes that you'll use Access for a standalone database application, or connect to its own SQL Server product or something like Oracle which is why ODBC exists.

---

### Post by Matthew_Harrop on 2015-03-29
I'm sorry, I'm used to dealing with Sqlite3 so the concepts of Oracle, MySQL and SQL server are a little alien to me.

---

### Post by SeijiSensei on 2015-03-30
Well the first thing that comes up from a Google search for "sqlite excel" is this:  [https://sqliteforexcel.codeplex.com/](https://sqliteforexcel.codeplex.com/)

Have you tried that?

---

### Post by ofnuts on 2015-03-30
SQLite is a bit incompatible with the requirement to share the DB with others...

---

### Post by Matthew_Harrop on 2015-04-07
Sorry I dropped off the face of the earth for a week, the run up to Easter was busier than I expected.

What we're going to do is: develop the program with the ability to connect to a local database (on the users computer) and a server based database (On a remote server, not on the users computer)

This will be specified by the installing engineer with the installer asking how/where/who would like to connect. I'm sorry for the confusion, I was still working the idea through in my head and needed some people to bounce ideas off. Thank you all for your help!

---

### Post by SeijiSensei on 2015-04-07
If I were starting from scratch, I'd build a browser-based application that connects to a web server with an SQL back-end and no local database.  That's the most portable solution and the easiest one to deploy.  If you need to interact in real-time with desktop applications, that won't work.  If all you need to do is exchange spreadsheets between the application and Excel or OpenOffice, you can use CSV files.

---

### Post by Matthew_Harrop on 2015-04-08
(Thankfully) The specification doesn't require real time updates otherwise, you're quite correct, It would be a browser based application. 
I'm adding the local dB for tiny companies or those who maybe can't afford the higher cost of a hosted solution - In development terms its not much different because I've scrapped the idea of using SQLite3 and will just use MySQL

---

