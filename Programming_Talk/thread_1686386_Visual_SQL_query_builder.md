---
title: "Visual SQL query builder"
date: 2011-02-12
forum: Programming Talk
---

### Post by .:PiXi²:. on 2011-02-12
Hi
Is there a decent tool for building SQL queries in a visual way available for Ubuntu?
I'm looking for something like the query builder from Visual Studio and SQL Server Management Studio, but for MySQL. Should I mention that I prefer free software? :)
Thanks in advance.

---

### Post by scott_tiger on 2011-02-12
phpmyadmin and MySQLAdministrator are two visual query builder..

Search more abut them over the net..

---

### Post by lallalla on 2011-02-12
is MySQL workbench what you are after? see [http://wb.mysql.com/](http://wb.mysql.com/)

---

### Post by .:PiXi²:. on 2011-02-12
Thanks for the replies scott and lallalla.
The tools you've suggested aren't new to me. I use phpMyAdmin almost on a daily basis and MySQL Workbench has replaced MySQL Administrator and MySQL Query Builder. It seems like I wasn't clear enough about what tool I'm exactly searching for. I don't need a tool which allows me to just execute a query on a database. I'm looking for a tool which not only gives the user a visual representation of the structure of the tables in a database, but I want a query builder that allows me to create joins and conditions in a visual way. I know these tools exist for Windows, but I would be so much happier with such a tools for Linux.

---

### Post by The Cog on 2011-02-13
OpenOffice / LibreOffice has a graphical query designer in its database application. It looks a lot like one I saw in MS access years ago.

---

### Post by .:PiXi²:. on 2011-02-14
I'll go with the query designer from OpenOffice, it seems like that's the best option.

---

### Post by WitchCraft on 2011-02-14
> **.:PiXi²:. said:**
> I'm looking for something like the query builder from Visual Studio and SQL Server Management Studio, but for MySQL. Should I mention that I prefer free software? :)
Thanks in advance.

Please please don't do that.
If you use such tools, you should be aware that they use foreign key references and NOT NULL restrictions to build their query.

The problem with that is that gives strange queries.
Usually it's coupled with human-unreadable SQL formatting, where you first have to format the SQL for 15 minutes before you can finally start to try understanding how the hell the query gets to the result (right joins because it starts with the wrong table, inner joins instead of left joins, etc...).

What's worse, when some of the restrictions change after the sql has been generated, (e.g. the not null vanishes), the query will be incorrect. 

Humans usually use understanding instead of restrictions as the base for building the query. 
So those bugs won't occur later.
The funny thing about this kind of bugs is, that they usually strike another persons than the one who commited the error in the first place...


I highly recommend you not using such tools, and I am talking specifically about the SSMS Query Builder, which is part of SQL Server, and not Visual Studio, BTW (an important difference, you won't be able to design SSRS 2005/2008 projects with VS 2010, for example). The server tools for Visual Studio always come separate with the SQL server, so you have to upgrade to Visual Studio 2008 if you want to work with SQL Server 2008. Or that you have to buy VS 2005 when you need to work with SQL Server 2005, although you may already have VS 2008/2010...

---

