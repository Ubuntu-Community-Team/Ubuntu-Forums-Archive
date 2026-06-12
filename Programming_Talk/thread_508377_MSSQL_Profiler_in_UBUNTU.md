---
title: "MSSQL Profiler in UBUNTU"
date: 2007-07-24
forum: Programming Talk
---

### Post by joe_net on 2007-07-24
hi.... could anyone.
i'm currently having difficulty in finding programs that are similar with MSSQL profiler that runs on UBUNTU, since my company is migrating to linux and our database is still using SQL server :(.
thank you all....

---

### Post by alanandhispc on 2007-07-24
Hi,

i don't think there will be any application like this for MS SQL. You can try mono for doing sql, but thats as far as it will go.

I suggest you look into just using remote desktop to access the database server directly and run profiler from there or investigate migrating to postgresql ([http://www.postgresql.org/docs/techdocs.3](http://www.postgresql.org/docs/techdocs.3)) or mysql ([http://dev.mysql.com/tech-resources/articles/migrating-from-microsoft.html](http://dev.mysql.com/tech-resources/articles/migrating-from-microsoft.html)) if possible. in terms of like for like migration, i would suggest postgres.

There are paid for support options with both companies and if your in the UK, [http://www.siriusit.co.uk/](http://www.siriusit.co.uk/) might be able to help... although there are plenty of other companies too.

Alan

---

