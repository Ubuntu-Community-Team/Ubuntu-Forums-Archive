---
title: "Adding data to database Through A Webpage"
date: 2007-12-04
forum: Programming Talk
---

### Post by TreeFinger on 2007-12-04
I am working with SQL on windows. I am wondering if anyone could direct me to any source of information that would help me add new data entries for a database from the web. It is just one table that I have to add. Also, deleting and modifying current contents would be a nice thing to learn about.

---

### Post by Wybiral on 2007-12-04
What language for the server-side code? PHP? Python? Ruby?

---

### Post by TreeFinger on 2007-12-04
Well this is for a class project. My teacher did a terrible job of explaining how to do this through a webpage. The entire semester we just learned about designing and querying a database. For our final project we must do this as part of our database. I believe she was showing us code in .ASP?

Not really sure..

---

### Post by teryowen on 2007-12-04
SQL and ASP are completely different.

As for doing the stuff with MySQL on windows install WAMP server, its a nice package to handle everythign and has an easy interface to do what you want to do.

[http://www.wampserver.com/en/download.php](http://www.wampserver.com/en/download.php)

Just download the WAMP sever, from there you will be able to use MySQL, and some premade php pages which will help you edit the database (although i dont use php, i use perl) 

EDIT: Heres a tutorial [http://www.w3schools.com/sql/default.asp](http://www.w3schools.com/sql/default.asp)

---

### Post by TreeFinger on 2007-12-04
Well I won't be setting up any servers. The Database is run on a server from our school. Our teacher tried to get us webspace from the school that was able to run scripts and all that junk but they didn't. She found a free hosting service where we could do it from.. I'm pretty sure the code she was displaying to us was a mix of .ASP and java script.. can't take my word for it though. I'll have to talk to the teacher. 

When Wybiral said Python I got really excited. I would like to do it in that if possible.

---

### Post by Wybiral on 2007-12-04
> **TreeFinger said:**
> When Wybiral said Python I got really excited. I would like to do it in that if possible.

The thing is that you need a script on the server that handles the actual SQL queries, then the webpage is just submitting requests to that script.

Python is very possible, but your server has to support it (apache, for instance has mod_python and is also capable of CGI with Python).

---

### Post by sethvath on 2007-12-04
[MS SQL]("http://en.wikipedia.org/wiki/Microsoft_SQL_Server") is probably the one you used in school on windows. It is different from [mySQL]("http://en.wikipedia.org/wiki/Mysql") which is more commonly found across web hosts. 

If you already have ubuntu installed I'll recommend you start with [XAMPP]("http://www.apachefriends.org/en/xampp.html") which is a [LAMPP bundle]("http://en.wikipedia.org/wiki/LAMP_%28software_bundle%29") with apache, phpmyadmin, mysql etc - tools you need to learn about databases. 

Look at some screenshots of phpmyadmin, if your teacher used some free host it is likely the host provided phpmyadmin.

---

### Post by evymetal on 2007-12-04
> **TreeFinger said:**
> Well I won't be setting up any servers. The Database is run on a server from our school. Our teacher tried to get us webspace from the school that was able to run scripts and all that junk but they didn't. She found a free hosting service where we could do it from.

You will need to use a language supported by that hosting service. In fact, to get the marks will you need to use the same language or scripts your teacher used?

---

