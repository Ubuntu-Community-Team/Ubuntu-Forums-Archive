---
title: "Gambas Programing  .dat file"
date: 2017-01-10
forum: Programming Talk
---

### Post by rx-mich on 2017-01-10
[SIZE=3] Hi, new to Gambas but not to basic programming. I see on the forum methods to open sequential file streams.... does Gambas support random file creation with a reference to  a file structure? Is the only way to do this require use of an SQL or can I freely design my own random file?   Example somewhere I can review?  Thanks[/SIZE]

---

### Post by col48 on 2017-08-21
I don't believe Gambas supports non-database random access files directly, but, as you say, SQL offers one approach.

I have what amounts to a database in a dozen (or so) text files (equivalent to database tables) in csv format.  The whole is under 10Mb and reads into Gambas arrays, including parsing, indexing and cross-referencing in about 5 seconds.  Each file has an initial line which contains coded field names which are recognized in the program, which makes for flexibility - simple program changes can add or delete fields, reorder them etc, and backup is achieved by rewriting edited files with distinct datestamped names.  Being csv also means I can look at the tables in a spreadsheet, as long as there are no more than 1024 fields!

Once in memory, finding "records" is a simple and fast process, of course.

Initially this was done in Visual Basic, but the csv format is highly portable, unlike most flavours of SQL database.

---

