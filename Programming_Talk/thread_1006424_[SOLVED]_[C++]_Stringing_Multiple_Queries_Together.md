---
title: "[SOLVED] [C++] Stringing Multiple Queries Together Using MySQL++"
date: 2008-12-09
forum: Programming Talk
---

### Post by dwhitney67 on 2008-12-09
Hi,

I'm trying to string together multiple queries together into one transaction, yet for some reason MySQL is unhappy with the query construct I am putting together.

Here's what I have attempted:
[php]
mysqlpp::Connection con;
con.connect(0, server, user, pass);
con.select_db(db);

mysqlpp::Query query = con.query();

query << "BEGIN; ";

query << "INSERT INTO " << table << " VALUES('VTRIX', 'Vanguard International Value Fund', 1500.00, 30.00, '2005-01-01'); "
      // ...
      << "INSERT INTO " << table << " VALUES('JORNX', 'Janus Orion Fund', 1500.00, 30.00, '2005-01-01'); ";

query << "COMMIT;";
query.execute();
[/php]

This is the error I get:
```

Error: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '; INSERT INTO stocks VALUES('VTRIX', 'Vanguard International Value Fund', 1500.0' at line 1

```

I've tried running the query without the BEGIN/COMMIT statements, but then I get an error indicating that the second INSERT statement is "wrong".

When I manually issued two insert queries together using the MySQL shell interface, then everything worked fine.

Thus I cannot figure out what is the issue with MySQL++.  Can anyone help?

---

### Post by dribeas on 2008-12-09
I have never used MySQL, but there is a chapter on [transactions]("http://tangentsoft.net/mysql++/doc/html/userman/tutorial.html#Transaction") in the MySQL++ docs. You don't just concatenate strings and then send one simple query, but rather create a transaction object and execute all separate queries before commiting/rolling back. 

This is the same mechanism that is used within Java, if I recall correctly. It's been long since I used both java and MySQL

---

### Post by dwhitney67 on 2008-12-09
Thanks for the reply.  I know/knew from past experience that MySQL++ allowed for multiple queries to be issued.  I dug through some old code (two years old) I have to verify this, but alas, what I found won't work because the folks who developed MySQL++ have changed their API.

Doing a little more research, I found that it is still possible to perform multiple queries by setting a particular option with the connection object.

So, should anyone else run into the problem I was having, here is the solution in a nutshell:

[php]
mysqlpp::Connection con(db, server, user, pass);


// Set option to allow multiple queries to be issued.
mysqlpp::MultiStatementsOption* opt = new mysqlpp::MultiStatementsOption(true);
con.set_option(opt);

// Build either single queries or multiple queries strung together.
mysqlpp::Query query = con.query();
....

// Issue query
query.store();

// Do NOT delete 'opt'; it will be destroyed by the 'con' object when it
// falls out of scope.
[/php]

---

### Post by cercaria on 2011-02-28
That's the 'table' name you have used in the Mysql script.
 
It should be in the quotes  :  'tablename'    ,
 
try this:
 
[FONT=Courier New][COLOR=#0000bb]query [/COLOR][COLOR=#007700]<< [/COLOR][COLOR=#dd0000]"INSERT INTO \' " [/COLOR][COLOR=#007700]<< [/COLOR][COLOR=#0000bb]table [/COLOR][COLOR=#007700]<< [/COLOR][COLOR=#dd0000]" \' VALUES('VTRIX'[/COLOR][/FONT] ......
 
 
i hope you got the point...

---

### Post by Iowan on 2011-02-28
[[img]http://s3.postimage.org/wwatx561a/Thread_Necromancer.jpg[/img]](http://www.postimage.org/)

---

