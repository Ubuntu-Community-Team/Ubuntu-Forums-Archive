---
title: "Learning SQL"
date: 2011-05-08
forum: Programming Talk
---

### Post by Aikifuku on 2011-05-08
I am trying to learn SQL and, more importantly, how it is supposed to be used. 

I can understand the syntax of SQL through tutorials. However, I am confused about how to run an SQL script. I have installed mySQL and SQlite3. 

As I understand it an SQL script can be fed into mySQL or SQlite3 from the command line and the output is then written to a database or the database is modified by the code. This can be done using a command like

$ sqlite3 data.db < script.sql

Is my understanding correct? Any advice or clarifications would be greatly appreciated. 

Thanks in advance.

---

### Post by rosencrantz on 2011-05-08
I don't know SQL, but your CLI code looks inverted to me:
$ sqlite3 script.sql > data.db
looks more like what you describe (pipe the output of sqlite3 interpreting script.sql into a database called data.db)

---

### Post by The Cog on 2011-05-08
Moved to programming talk. It will take longer to get buried there. You can feed sqlite3 a series of SQL commands from a script, but I would suggest that for learning SQL, an interactive command line would be more useful.

Just the command **sqlite3 data.db** will start sqlite3 and drop you into a command prompt where you can enter commands by keyboard. You may find the firefox add-on called sqlite-manager useful. It allows entering sql commands, but also does a graphical database editing.

P.S.
Sorry rosencrantz, but **sqlite3 data.db < script.sql** is the correct way to do this. sqlite3 takes the name of a database file as the first argument. If you are running an input script you could also redirect output like this: **sqlite3 data.db < script.sql > out.txt**

---

### Post by Aikifuku on 2011-05-08
> **The Cog said:**
> Moved to programming talk. It will take longer to get buried there. You can feed sqlite3 a series of SQL commands from a script, but I would suggest that for learning SQL, an interactive command line would be more useful.

Just the command **sqlite3 data.db** will start sqlite3 and drop you into a command prompt where you can enter commands by keyboard. You may find the firefox add-on called sqlite-manager useful. It allows entering sql commands, but also does a graphical database editing.

P.S.
Sorry rosencrantz, but **sqlite3 data.db < script.sql** is the correct way to do this. sqlite3 takes the name of a database file as the first argument. If you are running an input script you could also redirect output like this: **sqlite3 data.db < script.sql > out.txt**


Thank you very much. Does MySQL work the same way? Otherwise this answered my question.

---

### Post by The Cog on 2011-05-09
Not quite the same way. With sqlite, there is an application working on a database file - it's all kind of self-contained. 

With mysql, it definitely comes in two parts. There is a mysql server, which has no GUI at all, but just sits there and accepts connections from clients. And there are clients, that connect to the MySQL server, rather in the same way as a web server and web browsers. There are GUI clients such as **mysql-admin** (for administering users, tables etc) and **mysql-query-browser** (for querying/editing table contents), and also a command-line client like **mysql** which just allows you to type SQL commands such as **select from...** and **insert into...**. 

For learning, practice, testing and for single-user applications such as firefox (which uses several sqlite databases for storing passwords, cookies etc) it's probably easier to use sqlite. But it you want multi-user access such as in a ticket system, or multi-threaded access, then you really need a separate SQL server that can serve multiple SQL clients concurrently over a network, and this is where database servers such as MySQL, postgresql and Oracle (the big commercial one) come in.

---

### Post by PANGERAN on 2013-03-10
> **The Cog said:**
> ...You may find the firefox add-on called sqlite-manager useful. It allows entering sql commands, but also does a graphical database editing.

Thank you very much, The Cog! It helped me a lot to learn SQL from my netbook, by using firefox.

Thank you! :)

---

