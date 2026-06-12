---
title: "Database's?"
date: 2007-07-09
forum: Programming Talk
---

### Post by smilinmonki666 on 2007-07-09
Hello,

Not sure if I've come to the right part, but I've been asked to produce a database for a friend of mine but it needs to be available for both the Linux & XP OS.

I've only just come over to Linux the past month or so & haven't made a Database for a good while now. It needs to be a relational database with a customer section, a product section and enable the user to produce a sales invoice and link it to the customers account and print an invoice.

Does anyone have any suggestions? I would use OpenOffice Database, but want to check if anyone else has a suggestion before I learn the software & find something else that is better? Also, are there templates available?! Or even something where I could make a database & load it as its own program!?

Thank you in advanced

Smilinmonki666

---

### Post by twistedtwig on 2007-07-09
My question would be how portable does it need to be?

is it just that it needs to work on both OS's? or will it be regualarly moved from place to place?

if it is going to move about (or have the need to) then I would think something like open office / access would be sensible.

If it just needs to work across both somethign like MySQL could be a solution.

---

### Post by smilinmonki666 on 2007-07-09
It doesn't need to be portable, just availble for both operating systems.

---

### Post by loell on 2007-07-09
there is also kexi [http://www.kexi-project.org/screenshots.html]("http://www.kexi-project.org/screenshots.html") the touted as the microsoft access for linux :)

to install, via command line

```
sudo apt-get install kexi
```

i didn't read the whole post :(

but anyway, kexi is also available in windows, but for a price :(

---

### Post by smilinmonki666 on 2007-07-09
Thank you,

I will have a look at that. I just want to emulate an EPOS system, his companies just starting up, so something free at the moment.

---

### Post by EndPerform on 2007-07-09
Instead of trying to write your own, might I suggest searching for an open source invoicing system?  I believe there may be some, and you might find one that will do what he needs, and all you'd need to do is install it.

---

### Post by pmasiar on 2007-07-09
Very simple database (without server, just library calls) is SQLite. 

But all devend on how you plan to build your frontend. Desktop? web-based frontend? They are completely different approaches.

---

### Post by Dragonbite on 2007-07-09
[LIST]
[*][[COLOR="Blue"]MySQL[/COLOR]]("http://www.mysql.org/")
[*][[COLOR="Blue"]PostrgeSQL[/COLOR]]("http://www.postgresql.org/")
[*][[COLOR="Blue"]Kexi[/COLOR]]("http://koffice.org/kexi/")
[*]Base
[*][[COLOR="Blue"]SQLite[/COLOR]]("http://www.sqlite.org/")
[*][[COLOR="Blue"]Firebird[/COLOR]]("http://www.firebirdsql.org/")
[/LIST]

that's all I can think of off the top of my head.. I'm sure there are others out there.

---

### Post by smilinmonki666 on 2007-07-09
Thank you for the response.

I'm trying to find an open source epos system, but its finding something compatible on both. May only go for the linux, as he is very impressed with Ubuntu 7.04 I gave him, so he may use that?

I need it to be a simple desktop application, no web interface needed.

---

### Post by ankursethi on 2007-07-09
In that case, an SQLite back-end with the GUI front-end in some sort of RAD scripting language will be nice (Perl/Python/PHP). This setup is guaranteed to work everywhere. You can also use a full blown DB instead of SQLite if you want, like MySQL or PostgreSQL, but unless the size of his data is in several GB's, I think SQLite will be able to handle most requests.

---

### Post by timmie on 2007-07-17
I would like to ask in this context what database management applications you recommend.

I need to administer scrientific datasets easily including designs of forms and queries. As well I'd need to access PostgresSQL and MySQL databases.

I found that Kexi
* doesn't have a postgres-driver in Ubuntu: [https://launchpad.net/ubuntu/+source/kexi/+bug/61850](https://launchpad.net/ubuntu/+source/kexi/+bug/61850)
* crashes when I want to open a MySQL table

Furthermore I can access postgres tables with OOo Base but I am not able to use the query and from wizard.
OOo cannot access MySQL databases since the Java driver fails.

Can you give me a hint for my database management.

Thanks!

---

### Post by Dragonbite on 2007-07-17
I haven't use it in a long time, and I'm not sure if it is in the repositories but [[COLOR="Blue"]Aqua Data Studio[/COLOR]]("http://www.aquafold.com/") handles [LIST]
[*] Oracle
[*] DB2 UDB
[*] SQL Server
[*] Sybase ASE
[*] Sybase Anywhere
[*] Sybase IQ
[*] Informix
[*] PostgreSQL
[*] MySQL
[/LIST]and is available for  Windows, Linux, OSX, Solaris and Java[tm].

---

### Post by pmasiar on 2007-07-17
you need desktop or web-based admin? PhpMyAdmin might be something to research.

---

