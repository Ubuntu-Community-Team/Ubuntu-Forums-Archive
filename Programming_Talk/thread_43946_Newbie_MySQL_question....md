---
title: "Newbie MySQL question..."
date: 2005-06-23
forum: Programming Talk
---

### Post by MikeSTL on 2005-06-23
Hi All,

I have convinced myself that I need to lean MySQL. However, being completely new to MySQL and kinda new to Linux, I am a bit confused.

-what are my options in creating a front end for my MySQL database? I would prefer something as easy to learn as possible, and that would allow me to access the MySql database from a variety of platforms (Win, Mac, Linux)

Does this question even belong in this forum? If not apologies in advance...please direct me to the correct forum.

Thanks,

Mike

---

### Post by DJ_Max on 2005-06-23
This is the correct forum. And welcome to Ubuntu. MySQL is an ok DB. The easiest language to manipulate MySQL, and is cross-platform would be [PHP](http://php.net/). This is of course for web development.

---

### Post by MoneyCat on 2005-06-23
I'd suggest a very complete, concise tutorial on php & mysql: [http://www.php-mysql-tutorial.com](http://www.php-mysql-tutorial.com)

Also check out LAMP: [http://www.phpfreaks.com/tutorials/89/0.php](http://www.phpfreaks.com/tutorials/89/0.php)



Good Luck

---

### Post by LordHunter317 on 2005-06-23
If you want to learn how to use a RDBMS and proper relational data storage, I strongly suggest you do it on a real RDMBS, like PostgreSQL.  

MySQL's nonstandard behavior and odd coddling will just hurt you.  Understanding the real concepts first and then learning to adopt for MySQL's shortcomings will be a benefit to your knowledge.

---

### Post by DJ_Max on 2005-06-23
[QUOTE=LordHunter317]If you want to learn how to use a RDBMS and proper relational data storage, I strongly suggest you do it on a real RDMBS, like PostgreSQL.  

MySQL's nonstandard behavior and odd coddling will just hurt you.  Understanding the real concepts first and then learning to adopt for MySQL's shortcomings will be a benefit to your knowledge.[/QUOTE]
 I was going to say the exact samething, which is why I sad MySQL was just an ok DB. Learning MySQL & PHP will hurt you when learning other SQL vendors. MySQL stands out as an oddball. It doesn't really follow standards, while all the other DB servers do. It's easy for me to transfer a PostgreSQL DB, to say Oracle, but hard to transfer anything to or from MySQL.
TO be honest, I think MySQL is overly used.

---

### Post by LordHunter317 on 2005-06-23
Well, that's not really true.  Moving between PostgreSQL and Oracle is easy because PostgreSQL's dialect is closest to PL/SQL, and they frequently chose to model behaviors after Oracle (in the rare cases Oracle makes sense).

OTOH, moving PostgreSQL to MS SQL Server is a PITA.  Sure, they both support roughly the same set of features (at least from a programmer's perspective), but the performance is different in many aspects, and the syntax is very different, as SQL Server uses T-SQL.  

However, moving between Sybase and MS SQL is easy, because MS SQL is a child of Sybase.

DB2 is almost a complete oddball.

But the important thing to a programmer is that with all these databases except MySQL, I can treat the DB as an abstract component.  To the rest of my application, it doesn't matter if I use one query in PostgreSQL and another in DB2 to get optimal performance, because I can abstract that behavior away.  With MySQL, this is very difficult, and things that should be encaspulated and abstracted by the database itself have to be handled by the middleware logic.

Which for small projects and CRUD, doesn't matter much.  But for applications of any scale, it matters a lot.

That's ignoring all the fundamental features MySQL lacks or does wrong, too.

---

### Post by GrumpySimon on 2005-06-24
Mike_STL: If you don't want to write your own interface, there's a number of good front-ends available for MySQL. The most common one is [PhpMyAdmin](http://www.phpmyadmin.net/home_page/index.php) (but this will need to run via a webserver on your computer). There's also [GMyClient](http://freshmeat.net/projects/gmyclient/) which works in Gnome, and you can tell OpenOffice.org to  [use it as well](http://66.102.7.104/search?q=cache:qxgTF0qh9TwJ:www.unixodbc.org/doc/OOoMySQL.pdf+open+office+mysql&hl=en&client=firefox).

--Simon

---

### Post by MikeSTL on 2005-06-24
Hey guys,

Thanks for the input! I get the distinct feeling that there are strong opinions when it comes to which database to use...:)

I will be looking at both MySQL and PostgreSql...

Thanks again!


Mike

---

### Post by cow_racer on 2005-06-24
You could use mysqlcc which is a graphical mysql client.

---

### Post by frontline3k on 2005-06-24
Hi.
Just a thought: why not Firebird ? I'm a very happy Firebird user.
Fast, reliable, small size ... triggers, stored procedures ... and so on.
The most discussion I've seen are about MySQL / PostgreSQL. :? 

Take a look, give it a shot.
[http://www.firebirdsql.org](http://www.firebirdsql.org) / [http://firebird.sf.net](http://firebird.sf.net)

A cross-platform admin tool: [http://flamerobin.sourceforge.net/](http://flamerobin.sourceforge.net/)

For more info, take a look at [http://www.ibphoenix.com](http://www.ibphoenix.com).

Happy weekend.

---

### Post by DJ_Max on 2005-06-24
[QUOTE=frontline3k]Hi.
Just a thought: why not Firebird ? I'm a very happy Firebird user.
Fast, reliable, small size ... triggers, stored procedures ... and so on.
The most discussion I've seen are about MySQL / PostgreSQL. :? 

Take a look, give it a shot.
[http://www.firebirdsql.org](http://www.firebirdsql.org) / [http://firebird.sf.net](http://firebird.sf.net)

A cross-platform admin tool: [http://flamerobin.sourceforge.net/](http://flamerobin.sourceforge.net/)

For more info, take a look at [http://www.ibphoenix.com](http://www.ibphoenix.com).

Happy weekend.[/QUOTE]
Thats because not many people have used Firebird, neither have I, so I can't give him a recommendation on something I've never used. I was really trying to get him to use something besides MySQL.

---

### Post by LordHunter317 on 2005-06-24
Firebird isn't as refined as PostgreSQL in many ways and has some serious inline storage limitations.  That being said, it would be OK for learning, but would add what mostly unnecessary tedium to the project.

---

