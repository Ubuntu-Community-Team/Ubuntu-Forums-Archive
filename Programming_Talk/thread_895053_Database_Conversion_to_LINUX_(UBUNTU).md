---
title: "Database Conversion to LINUX (UBUNTU)"
date: 2008-08-19
forum: Programming Talk
---

### Post by Steve R. on 2008-08-19
I currently have an ACCESS database.  I now have a UBUNTU test platform so I am looking at my options for migrating the database to a LINUX computer. However, I am not familiar with what components I would need on my UBUNTU computer to run a LINUX database.

1. I could use WINE.

2. There is MySQL and Base, but I am not familiar with them.  It appears that MySQL and Base may need additional programs to actually access the data. Fore example, in ACCESS you use a combination of VBA, DAO, and SQL to access the data and display it. I assume the same situation exists for MySQL, but I am not familiar with what these other programs would be (Python for example?) Or to put this a different way, what do I need for a "Front End" to access the data and which would be the best database for data storage (Back End)???

---

### Post by mike_g on 2008-08-19
You can always convert an access database to mysql. I used this free tool in the past to do it:
[http://www.bullzip.com/products/a2m/info.php](http://www.bullzip.com/products/a2m/info.php)
Then did the rest of the work with phpMyAdmin. The only thing that might be a problem is that you lose your queries, forms and stuff.

---

### Post by pmasiar on 2008-08-19
Access database: I assume MS Jet db engine, right? Classical vendor lock-in.

As you found out VBA is not a flexible multiplatform  option. :-)

Do you want single-user desktop app, or web-based app?

Python is excellent simple and flexible language, optimal for both tasks (see wiki in my sig for links).

If your needs are simple, SQLite is much simpler to manage than full blown DB server like MySQL. And is included in Python 2.5.

For very simple desktop GUI, try Python' EasyGUI. For web app, Django is excellent, and comes with web server simpler than apache.

---

### Post by mssever on 2008-08-20
> **Steve R. said:**
> 2. There is MySQL and Base, but I am not familiar with them.
If you can make OOo Base actually work for you, you're smarter than I am. OOo would be better off just using SQLite than their abomination of a database.

---

### Post by Zugzwang on 2008-08-20
> **mssever said:**
> If you can make OOo Base actually work for you, you're smarter than I am. OOo would be better off just using SQLite than their abomination of a database.

Oh, they *do* use a non-custom database implementation, it's just not SQLite: HSQLDB - However, the actual database files are hidden in the .odb (?) file. Since .odb (?) files are however .zip files, you can easily extract them. The question is whether Oo Base is mature enough to actually use it. The last time I tried Base, I lost all of my data two times.

EDIT: OP, have you tried "Kexi"? It is part of the KDE office apps and it looks like as it can open databases made using MS Access. Maybe that works for you?

---

