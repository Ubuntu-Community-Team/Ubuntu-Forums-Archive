---
title: "sql in html"
date: 2007-05-29
forum: Programming Talk
---

### Post by jeff00z28 on 2007-05-29
This might be a stupid question or impossible but programming type of stuff isn't my specialty. I made a database in phpmyadmin and would like to put the table on an html page. I would still like to be able to sort by columns etc, but not have to run a queery every time i want to see teh table. If any1 has any suggesitons or advice pleasle help thanks.

---

### Post by jeff00z28 on 2007-05-29
i should have mentioned this is in ubuntu

---

### Post by Rogers on 2007-05-29
Go do a search on SQL queries via PHP on google.  There are hundreds of pages that can help you.  I suggest doing google search before posting to a forum. It will save you a lot of time. ;)

---

### Post by jeff00z28 on 2007-05-29
i know how to run a queery thats not what i was asking. im tryin to make something like this only in linux

[http://www.activewidgets.com/javascript.forum.18629.0/loading-data-from-a-table.html](http://www.activewidgets.com/javascript.forum.18629.0/loading-data-from-a-table.html)

---

### Post by pmasiar on 2007-05-29
> **jeff00z28 said:**
> im tryin to make something like this only in linux

Linux, ubuntu, whatever - thats irrelevant. Your problem is understanding how web server, PHP and SQL database work.

Every time you want different HTML page (like sorted by different field), web server needs to generate it. You may try to cache the data but IMHO it makes no sense and would be prohibitive.

You also can try AJAX and re-sort submitted data on client side using JavaScript, but I doubt you have a clue how to do it or what I am talking about :-)

In short, what are you trying to accomplish, and what are your reasons?

---

### Post by barmazal on 2007-05-29
> **jeff00z28 said:**
> i know how to run a queery thats not what i was asking. im tryin to make something like this only in linux

[http://www.activewidgets.com/javascript.forum.18629.0/loading-data-from-a-table.html](http://www.activewidgets.com/javascript.forum.18629.0/loading-data-from-a-table.html)


HTML is static language you cannot access via it to database, doesn't matter you know queery or big gay al.
you cannot access database within Javascript since it's client script and database is server application.

you can access database from server side language/script such as php, asp..... and so on...

what you have there called AJAX it uses PHP to retrieve data from database and Javascript+HTML to format it for your view when Ajax functionality just gives you ability to modifying database locally without reloading page  when request sent

---

### Post by jeff00z28 on 2007-05-29
ok i understand it a little more I am more into networking but was asked to do this at work. they just wanted a database made but they wanted to be able to see it on an html page but i dont see how thats possible

---

### Post by jeff00z28 on 2007-05-29
ur right about me not knowing what databases involve lol. I took a class on sql server a few years ago a high school class so i know how to code it but i never rly understood completely how everything works and how it applies to things.

---

### Post by jeff00z28 on 2007-05-29
is there a way to like embed something onto an html page that links to the database but somehow displays its table?

---

### Post by Mirrorball on 2007-05-29
It happens everytime you send a message to this forum or read a topic or see a list of threads... The answer is PHP.

---

### Post by barmazal on 2007-05-29
> **jeff00z28 said:**
> is there a way to like embed something onto an html page that links to the database but somehow displays its table?

that would be hell long explanation. it's like giving me an explanation on how create 3D human hand. I know Photoshop but not Maya or 3Dmax to actually create model hand png should lay on.


in theory you should have database on page called something.php you should open connection to database, retrieve what you want to have and style it using html and some php programming functionality like running loop for table creation from 2d array. 
This page will be rendered into HTML page when user come to your web server, of course if it supports php.

---

### Post by airtonix on 2007-06-15
it is infact possbile to use javascript and html on the client utilising the following 

SQL queries.
JsTemplating system
Flat File Databse

investigate : [trimpath]("http://trimpath.com/") a Model / View / Controller [SPADE]("http://code.google.com/p/trimpath/wiki/SinglePageApplicationAndDevelopmentEnvironment")
demo : [nextaction]("http://trimpath.com/demos/nextaction_static1/nextaction.htm") a SPADE application

Further the usefulness of this trimpath framwork with XULRUNNER, thus giving it platform promiscurity

---

