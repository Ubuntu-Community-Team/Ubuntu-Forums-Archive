---
title: "Database management tools"
date: 2007-02-02
forum: Programming Talk
---

### Post by slevino on 2007-02-02
Hi,

I'm a newcomer to ubuntu (and linux) and I'm having fun learning how to do things in a non-windows world. Unfortunately I can't shed the redmond devil entirely and so I need some advice on how to manage MS sql servers from within ubuntu. 

My company has several MS sql 2000 servers installed and I'd like to be able to connect to them from my ubuntu machine, query the database with T-Sql, add tables, write stored procs, etc. Is there a database management tool (analog of query analyzer) that will allow me to this? If so, what are the options?

Thanks for any help offered and appologies if this is something I should know already (or if this is the wrong forum).

Shelby

---

### Post by marianom on 2007-02-02
A quick option I can suggest you is [Oracle's Sql Developer]("http://www.oracle.com/technology/products/database/sql_developer/index.html"): it's free, it's written in Java and it has support for Sql Server (you just need to add the JDBC driver from microsoft site, which it seems free too).
I cannot guarantee in what extend it will let you work but probably you could query tables and modify T-SQL code.

---

### Post by slevino on 2007-02-03
Thanks Mariano. I'm looking into that now!

---

### Post by marianom on 2007-02-03
Please, whenever you have the time, let me know how it goes. 
Eventually my crimes will be punished and I'll have to deal with certain t-sql code I wrote a long time ago. I just wanna be ready.

---

