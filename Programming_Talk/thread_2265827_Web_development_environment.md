---
title: "Web development environment"
date: 2015-02-18
forum: Programming Talk
---

### Post by alex317 on 2015-02-18
Hello!,I want to start using Ubuntu for web development and i would like to know some alternatives i can use instead of Easyphp and MySQL front (those are made for the Windows platform.) so basically i need a local server and a database editor that are fairly simple to use for a beginner.
I asked for help on this forum because I could Google the information,but would be nice to ask some professionals.
Thanks for your interest and for taking the time to read my question.

---

### Post by TheFu on 2015-02-18
I use vim or geany and mariadb or postgres for my perl wsgi webapps. If you use an ORM for DB access, you don't need much DB knowledge until it comes time to tune. Then only a few queries need to be touched. Writing direct SQL is so ... 1995.

Also use vim or geany for Ruby on Rails development. If I did python webapps, I'd use vim or geany for that as well.
There is a turn against MySQL by many companies.  MarieDB is the drop in replacement from the same team that created MySQL ... they all left Oracle and have created something in MariaDB that is really great for their clients - and us.  14.04 APT dependencies see mariadb as a dropin replacement for mysql.  The perl and Ruby communities have been migrating towards postgres because have more features of classic RDBMS - it is ACID compliant, unlike MySQL.  Here, we start with postgres as the target DBMS, but with most web frameworks and ORMs, it isn't too hard to swap the DBMS. Best to start with the same one you will deploy into production. Postgres is available at most hosting companies, so it isn't a big risk to use it.

We don't do php development.  Please be aware: [https://www.owasp.org/index.php/PHP_Security_Cheat_Sheet](https://www.owasp.org/index.php/PHP_Security_Cheat_Sheet)

Linux is like Unix and the entire OS is a development platform. The platform is an IDE, so no 1 program is used by the experts I know - except java devs, who seem stuck using Eclipse for some reason that doesn't make any sense to me.  I don't have enough RAM to use eclipse.

Should also say that vim is probably the most advanced editor in the world today. In the hands of an expert, it blows away emacs or eclipse for editing facilities - plus it isn't slow and RAM sucking. I used emacs in the old days, but as I learned more and more of vi/vim, found myself telling emacs to go into vi-mode more and more. After about a year, I simply stopped using emacs and never looked back. Geany is a nice, light-weight, cross-platform, editor sorta like notepad++.

---

### Post by flaymond on 2015-02-21
I don't develop web platform , but this might help you.

LAMP - [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

and if you want a good IDE for developing web, try Bluefish Editor.

* I use vim a lot (learn the basic commands is already enough for beginning) because it's fast, simple and you can access it directly in Terminal. (Gonna help you when you need something to be accomplished fast in Terminal)

* If you want a very powerful text editor but don't mind to learn - try Emacs



Thanks.

---

### Post by pc_magas on 2015-02-23
For my development I use Aptana Studio [http://www.aptana.com/](http://www.aptana.com/) Is rather good for php and Javascript. But it not good enough for Html parsing. Usually a web dev in Greece is a full stack and does enverything from backend to frotnend.

---

