---
title: "Perl, DBI and SQL: Searching"
date: 2007-11-18
forum: Programming Talk
---

### Post by trevorv on 2007-11-18
I'm working on my first project with SQL, and am writing a very basic bookshop website. I have a Postgres database full of books, and am trying to write the search engine. I'm using Perl and DBI, and can find nothing on the net about how to search SQL databases! If someone could just give me some hints I'd really appreciate it.

Is the best method through a big wodge of SELECT statements? I'm lost where to start at the moment.

Help appreciated! Thanks!

---

### Post by pmasiar on 2007-11-18
Searching SQL database has nothing in common with Perl. SQL is language by itself.

More modern web application frameworks use object-relation mappers (ORM), creating object from table, with method to search etc, but I am not sure what current "state of the art" in Perl ORM is. Last time (couple of years ago) it was like all in Perl - "there is way too many ways to do it" :-)

Good simple MVC (Model-View-Controller - see wikipedia) web app framework was CGI::Application, but I don't follow it anymore. There are many many more frameworks, more complicated, IIRC Maypole, Mason and more. Google for "Perl web framework"

My suggestion would be to switch to Python (which is basically Perl done right, and with cleaner syntax), and use one of leading web app frameworks, like Django or TurboGears, each of them comes with decent ORM. 

TG's ORM, SQLObject, is so simple that I know about hacker who developed website relying on SO entirely, without learning any SQL at all. :-)

---

### Post by slavik on 2007-11-18
The way you search a database is by getting information out of the database and then doing something with the results.

One way would be to write a query builder, one of those where the person can select to search for an author and input what their name should look like. Of course, you should also read up on how spell checking is done so that you could return a list of likely authors that the user might be talking about (and mispelled their name).

NOTE: that is what I think the solution should resemble.

---

### Post by CptPicard on 2007-11-18
And do consider adding some sort of fulltext indexing module to PostgreSQL so you can do free-form searches on description texts and the like... I know they're there, just have never used one.

(Congrats on your choice of database... I can see the Force is with you.)

---

