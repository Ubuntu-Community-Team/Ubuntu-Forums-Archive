---
title: "Error 1044 in my server's phpmyadmin"
date: 2011-01-19
forum: Programming Talk
---

### Post by skytreader on 2011-01-19
Is there anyone here with using phpmyadmin with cPanel in managing a site? I need some help...

When I try to create/import a database to my server, I get the message

#1044 - Access denied for user 'myusername'@'localhost' to database 'mydatabase'

A CREATE TABLE statement is specified above as the line which threw the error.

I was only able to create when, at cPanel, I clicked on MySQL(R) Databases and from the resulting screen I added a new user (of form myusername_name) then added a new database with name of the form myusername_databasename .

The database myusername_databasename can now be accessed and manipulated from phpmyadmin but I still can't run CREATE TABLE queries. By the way, the user recognized by phpmyadmin is myusername@localhost. And I can't seem to find the tab for managing users. (I can see it in XAMPP but not in my server).

I'm sorry if my details are quite vague; it's my first time using a database on my server. Any help is appreciated. Thanks.

---

