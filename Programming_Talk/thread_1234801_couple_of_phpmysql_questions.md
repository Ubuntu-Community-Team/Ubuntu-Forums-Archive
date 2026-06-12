---
title: "couple of php/mysql questions"
date: 2009-08-08
forum: Programming Talk
---

### Post by Bulletbeast on 2009-08-08
Hi guys. Got to ask a couple of things, since I have no experience in building a PHP/MySQL driven website:
1. If my site is meant to have many user accounts, much like a forum, and the MySQL isn't directly exposed to the user, do I create a MySQL user for every user of my website, do I have different MySQL users with different access levels depending on the purpose they are used for (e.g. 'news' to display the news on my front page, regardless if the user is logged in, 'admin' to create user accounts, etc.), or can I go with a singe account with full SELECT/INSERT/DELETE/UPDATE/FILE privileges over data to do all database-related work?
2. Should I have a persistent connection to the MySQL server as a global variable, or connect every time I need to do a query, or connect once per page? On a side note, although my site is structured as an index.php which includes different pages depending on a _GET variable, can I have a global variable in PHP which spans over multiple separate (i.e. not including/requiring each other) PHP files?

---

### Post by Tibuda on 2009-08-08
1. One account per site is what I have always done. I see no reason to have one account per user, as all queries are done by your php code, unless you let the users to write their own SQL queries, which is not safe.

2. I use one connection per request. You can initialize it in one main file included in the other files. You can also use your 'index.php' structure and do something like this:

[php]<?php
# Open DB connection
# Render content based on $_GET
# Close DB connection
?>[/php]

---

### Post by Bufke on 2009-08-08
It's not a bad idea to have more than one mysql account.  So that each type of user only has the access they need.  The only advantage is that if you screw something up or someone uses sql injection, it might mitigate the damage.  But honestly a lot of people/companies just have one account and for a small obscure website thats fine.

---

### Post by slaiyer on 2009-08-08
As others said before, its much simpler to stick with one user, and let your php coding handle the permission issuing. Plus, i do believe your users will need access to sql (eg, forum).

As for connections, i would say dont use presistent connection (personal opinion). not really necessary.

---

### Post by hockey97 on 2009-08-08
> **Bulletbeast said:**
> Hi guys. Got to ask a couple of things, since I have no experience in building a PHP/MySQL driven website:
1. If my site is meant to have many user accounts, much like a forum, and the MySQL isn't directly exposed to the user, do I create a MySQL user for every user of my website, do I have different MySQL users with different access levels depending on the purpose they are used for (e.g. 'news' to display the news on my front page, regardless if the user is logged in, 'admin' to create user accounts, etc.), or can I go with a singe account with full SELECT/INSERT/DELETE/UPDATE/FILE privileges over data to do all database-related work?
2. Should I have a persistent connection to the MySQL server as a global variable, or connect every time I need to do a query, or connect once per page? On a side note, although my site is structured as an index.php which includes different pages depending on a _GET variable, can I have a global variable in PHP which spans over multiple separate (i.e. not including/requiring each other) PHP files?


You can do all what you said. I call this stage the website structure designing phase. You need to figure out what kind of website it is that you are making. Like it depends on what kind of site your making. I mean their is a big difference in a website just having a board form or blogging type site then a website that offers hosting services.

Just keep in mind about  memory space and bandwidth. Those are a huge factor on how you structure your site. 

My suggestion/opinion would be to use one single mysql user that will do all the querying. I would think you should connect  to the mysql server when being used and once it's not being used disconnect the connection. That means  don't connected per page. or reconnect per page. What you should do is connect once per session. So if your user logs in have the code to connect to the mysql server. Then when they are logging out then disconnect them from the mysql connection. 

Like I said it's just my opinion. Their is no right or wrong answer on this.I would suggest to try and disconnect the user from the mysql server whenever the user is not going to use it for a while.Key point is that when a user connects to the mysql server it's hogging bandwidth to the mysql server. This can cause slowdowns or a crash of some sort.So you need to make sure how many users can connect at a time with your sever. If you don't feel like finding that out then the golden rule here is that if the user dosen't need to query the database for a while then disconnect them from it. Kinda like why leave the lights on when your not using it, your wasting money and resources. In this case it would just be resources.So I am going with the connect/reconnect per page. I am saying this lightly. You should know when to connect and disconnect a user from the database. 

How I have my website setup. Is that the user is connected to mysql from the start of the login. Then when the user logs out or when their is at least 1 hour of in activity. I log them out and during this process I disconnect them from the mysql server.

---

### Post by Bulletbeast on 2009-08-08
> **slaiyer said:**
> Plus, i do believe your users will need access to sql (eg, forum).

What I meant was that they are not going to *see* it.

Thanks, guys.

---

### Post by jeffathehutt on 2009-08-09
> **Bulletbeast said:**
> Hi guys. Got to ask a couple of things, since I have no experience in building a PHP/MySQL driven website:
1. If my site is meant to have many user accounts, much like a forum, and the MySQL isn't directly exposed to the user, do I create a MySQL user for every user of my website, do I have different MySQL users with different access levels depending on the purpose they are used for (e.g. 'news' to display the news on my front page, regardless if the user is logged in, 'admin' to create user accounts, etc.), or can I go with a singe account with full SELECT/INSERT/DELETE/UPDATE/FILE privileges over data to do all database-related work?


Generally, you only need one database user per site.  On a site such as a forum, the database access is only done by your scripts, not directly by the users.  Adding more users makes it more complicated and rarely is there a need to do so.

> 
2. Should I have a persistent connection to the MySQL server as a global variable, or connect every time I need to do a query, or connect once per page?

This one is a bit tougher to answer.  Having many active database connections can certainly slow your system down, due to the increased RAM needed to maintain the connections.  On the other hand, constantly connecting, disconnecting, connecting, etc. can also slow your system down, due to the increase in processing power needed to connect.  The best answer really depends on how your site is set up, how much traffic it gets, etc.  There is no real answer that satisfies all sites.


> On a side note, although my site is structured as an index.php which includes different pages depending on a _GET variable, can I have a global variable in PHP which spans over multiple separate (i.e. not including/requiring each other) PHP files?

If you just need a simple way to track a variable, you could always set a cookie on each visitor's browser (assuming it doesn't matter if the cookie value is public).  If you need something more powerful, such as a way to save the visitor's state between visits, you can use the built in session functions in php.

---

### Post by slavik on 2009-08-09
1. no user comming to your site needs an account for your database ... you do not have a mysql account on the ubuntuforums.org database. you will need code to authenticate and authorize the user.
2. you might want to keep a pool of open connections (which would need to be checked in case they go bad). opening a connection every time puts a load on the DB, it will also increase latency to fulfilling a request.

---

### Post by Wim Sturkenboom on 2009-08-09
I have 3 classes of mysql users for a website that I host externally. The first one is for ordinary visitors that only need to retrieve data from the database. The second one is for visitors that need to be ableto update the site's content. And the last one is for an administrator.

[LIST=1]
[*]user visitor with only select privileges
[*]user members with select, insert and update privileges
[*]user admin with all privileges
[/LIST]

The first one is obvious; they can only read but never modify.
The second one can do a little more. In my case I don't want to be nagged by someone who accidently deleted an entry in a table, so I've opted not to allow them to delete. Instead, the tables have a column indicating if an entry is visible or not.
The third one can do anything and will at occasion check the 'invisible' entries and remove them.

The database itself has a 'users' table that allows each member to login with their own credentials. After successful login, a session variable is kept to link this user to one of the mysql users described above. The same table users is used for permissions to modify certain pages on the site.

---

### Post by Mirge on 2009-08-09
> **Wim Sturkenboom said:**
> I have 3 classes of mysql users for a website that I host externally. The first one is for ordinary visitors that only need to retrieve data from the database. The second one is for visitors that need to be ableto update the site's content. And the last one is for an administrator.

[LIST=1]
[*]user visitor with only select privileges
[*]user members with select, insert and update privileges
[*]user admin with all privileges
[/LIST]

The first one is obvious; they can only read but never modify.
The second one can do a little more. In my case I don't want to be nagged by someone who accidently deleted an entry in a table, so I've opted not to allow them to delete. Instead, the tables have a column indicating if an entry is visible or not.
The third one can do anything and will at occasion check the 'invisible' entries and remove them.

The database itself has a 'users' table that allows each member to login with their own credentials. After successful login, a session variable is kept to link this user to one of the mysql users described above. The same table users is used for permissions to modify certain pages on the site.


I like this setup. I would honestly say that for a smaller site receiving little traffic, a single mysql login would suffice. The above setup is pretty good, IMHO, though.

As for the hidden entries, I'd probably just make them automatically expire after they've been hidden 'x' amount of days (ie: every 30 days).

EDIT: Since you have no experience with PHP/MySQL, stick with a single MySQL account.

---

### Post by slavik on 2009-08-09
what is the MySQL database for and who are these external users that need access to it?

---

