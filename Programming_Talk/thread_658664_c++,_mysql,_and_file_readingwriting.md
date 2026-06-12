---
title: "c++, mysql, and file reading/writing"
date: 2008-01-04
forum: Programming Talk
---

### Post by t3hi3x on 2008-01-04
OK. This is more of an advice than help question, but there is some help involved.

I am creating an application that reads MP3 files and stores the tags in a MySQL DB. I can currently read one song at a time, but that isn't too efficient as i have ~30,000 songs. I need some advice:

Should I run a query each time I add a song? I feel this could be hard on the server, especially if I were to run the MySQL server on a box over the internet. Would it be better to create one huge query and upload it to the server (.sql file)?

I think that would be better because the program would generate the file, upload the huge query, and the server would execute it all at once.

The only thing I am concerned about is killing the entire program by running a potentially very large .sql file, not to mention I don't know how to get it to the server.

Anyone have some suggestions?

---

### Post by cmnorton on 2008-01-05
You can run the SQL file using MySQL's own tools and interfaces. That is your C++ code would create the SQL queury, perhaps even reading from a file or from a table in the same remote database, and then you have to run some kind of "prepare", so the database knows about it. Then you can run it.

It is very similar to how MSSQL and Informix work. The syntax of course is different, but the intention is the same.

If you are woried about speed, do performance measurements on how a stored procedure would run (to do the insert) versus a prepared statement.

---

### Post by t3hi3x on 2008-01-05
2 questions:

What is that prepare command? It seems like it would help.

Is there a way i can upload that sql file using c++? The toolkit I am using is mysql++. I think I could just load the file into a string and send the query that way... But if its several MB than it can't be good to throw all that into memory and try to send the whole thing.

Does anyone know mysql++ well enough to do this the right way?  The documentation for the toolkit isnt the greatest...I had to use the examples to figure out how to use it.

Thanks for the help.

---

