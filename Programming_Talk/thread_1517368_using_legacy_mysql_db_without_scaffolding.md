---
title: "using legacy mysql db without scaffolding"
date: 2010-06-24
forum: Programming Talk
---

### Post by railsfan on 2010-06-24
Hi All,
Here is my roadmap for my first app in ruby:
1) installed vbox and have ubuntu 10.04 lucid as guest os
2) using apache, passenger , mysql and ruby on rails.
Installed all of them separately. so this is the stack i'm using.
i'm originally well versed in oracle /ms sql db design and pgm.
so, created my backend db using mysql workbench (first time using mysql workbench. It is isn't like erwin but does the job for mysql)
Created my model in mysql wbench and generated the sql script file for creating tables. this is done.
Installed phpmyadmin and using the gui of it for mysql gui purposes.
Imported the sql script via phpmyadmin and the database is completed with all its structure.
 
Now, I wanted to use this backened db and use it for ruby on rails web app.
My web app is a simple web app which has only seven tables and relationships within it and it exists only in mysql db right now.
 
i created the structure using
rails -d mywebapp mysql
executed
ruby script/server
and the web app is up and running with the default page.
 
now, i have a table called category in mysql db and want to get the CRUD pages in ruby on rails web app.
I really hate to retype all my column names in the scaffold command.
so i want to skip migration in rails.
so i ran the command
script/generate scaffold category -- skip-migration
but this doesn't seem to have created any CRUD pages for the table category in mysql db.
 
What should i do to see the CRUD pages for the table category ?
By CRUD, i mean the create category, edit category, delete, etc.
I am avoiding the scaffold command because i hate to type all my column names in that command line.
Can I avoid that ?
Is there a way out?
Please help.
 
 
- Thanks
Radha
 
Keywords: Legacy My Sql db, avoid scaffolding, no need to retype all column names in scaffolding line, skip-no-migration
what is the solution for not scaffolding and getting the crud pages?
Is there a step by step approach elsewhere i can follow?

---

