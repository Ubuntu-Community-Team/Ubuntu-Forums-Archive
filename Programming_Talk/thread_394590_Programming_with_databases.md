---
title: "Programming with databases"
date: 2007-03-27
forum: Programming Talk
---

### Post by PLIACHAS PASCHALIS on 2007-03-27
First of all i have to say that i'm new in Linux environment. i used to programm in windows with Vb .net and used ADO to get access to databases. i'd like to ask the community (if it is possible first of all) how can i do such things in Ubuntu. which language i coud use to programm in visual environment and get access to databases. 
Sorry for my English and Thanks for help.

---

### Post by Wybiral on 2007-03-27
MySql is a really common open-source database. There are API's for it in a number of languages, so take your pick!

Have a look: [http://dev.mysql.com/doc/refman/5.0/en/apis.html](http://dev.mysql.com/doc/refman/5.0/en/apis.html)

---

### Post by PLIACHAS PASCHALIS on 2007-03-27
thanks for your reply. ok about the mysql which is (if i understood well) the language who provides access to databases. Which is the tool that anybody could use to show the records of a table in a form? 
Thanks again.

---

### Post by lnostdal on 2007-03-27
I use [PostgreSQL]("http://www.postgresql.org/") as database, with [pgAdmin]("http://www.pgadmin.org/") to "visually" view/edit the DB.

For the programming part I use Common Lisp ( [http://sbcl.sourceforge.net/](http://sbcl.sourceforge.net/) ) and CLSQL ( [http://clsql.b9.com/](http://clsql.b9.com/) ).

---

### Post by pmasiar on 2007-03-27
> **PLIACHAS PASCHALIS said:**
> mysql which is (if i understood well) the language who provides access to databases. Which is the tool that anybody could use to show the records of a table in a form?.
MySQL is database server. Another popular is PostgreSQL. Language is plain old SQL. :-) 

To access data in database, pick your choice of language: all of them have libraries to access SQL databases.

To show data you can use HTML over web, or there are plenty of libraries for desktop - what do you need? 

Visual basic and whole .NET framework are proprietary Microsoft products, and MSFT did not ported them to Linux. We have once-a-week rants/flamewars about why and what should developers of free software do about it, see: [ Futile Hope: MS Visual Studio .NET on Ubuntu?](http://ubuntuforums.org/showthread.php?t=393266) and [Linux better OS for Dev Then Windows?](http://ubuntuforums.org/showthread.php?t=315875)

Edit: oh yes visual anvironment. Many developers are very dedicated to their editor of choice, either vi/vim or emacs, customized it heavily and will never part with it to use inferior "standard" editor from VS. Check ie thread [ a simple ide for c++](http://ubuntuforums.org/showthread.php?t=392958) And then there are about 3 dozens of "lesser' simpler editors, which are on par with editor in VS. So you have a lot of choice. You need to select language first - Basic is not very popular. Popular choices are Python, Perl, Ruby, C, C++, and maybe Java. And of course many many other languages, just browse Synaptic. Every language has pro and cons, usage depends on what  kind of application you want to create, and what your team prefers/has skills/can handle.

---

### Post by PLIACHAS PASCHALIS on 2007-03-27
thank you all for your replies. i agree that is difficult to change from one day to another the IDE you are working with. i' ll take a look at your proposals and i'll try to decide.
thanks

---

### Post by Mirrorball on 2007-03-27
I think Java with Netbeans is the closest thing to .NET with Visual Studio.

---

### Post by Ozitraveller on 2007-03-27
I found these, hope they are useful.

Mono + MySQL
[http://www.mono-project.com/MySQL](http://www.mono-project.com/MySQL)


Mono + Database Access
[http://www.mono-project.com/Database_Access](http://www.mono-project.com/Database_Access)

Good luck
:)

---

