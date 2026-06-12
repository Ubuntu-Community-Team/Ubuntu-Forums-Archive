---
title: "Microsoft sql server and jdbc"
date: 2016-12-16
forum: Programming Talk
---

### Post by 1clue on 2016-12-16
Hi,

I just saw here: [https://www.microsoft.com/en-us/sql-server/sql-server-vnext-including-Linux](https://www.microsoft.com/en-us/sql-server/sql-server-vnext-including-Linux) that you can install Microsoft SQL Server directly on Ubuntu 16.04.

This is interesting to me because I need to develop against Microsoft SQL Server for my work, and it could presumably eliminate an otherwise unnecessary Windows license.

So I installed it, following the yellow brick road from the above page. I installed mssql-server and mssql-tools, and so far as it goes it appears to work.

The problem is, I'm having trouble with the jdbc connection. The same setup that works against mssql 2008-2014 will not work against this database. It appears that the driver may need to be changed, I'm using the **jtds 1.2.5** driver.

I tried using Microsoft's driver referenced in the documentation from above, but maybe my connection string isn't right?  **jdbc:sqlserver://*<dbserver>*:1433/*<database>***

Anyway, I was hoping someone else here had already figured this out and could lend a hand.

Thanks.

---

### Post by Rocket2DMn on 2016-12-17
IIRC, jtds 1.2.5 is pretty old.  There are newer versions available, but I'm not convinced that would be the problem.  At the risk of being unhelpful, I haven't used SQL server in years, or at all on Linux, but if you're running the SQL server on a different system, perhaps it's just that the correct ports aren't open?

Additionally, looking at the video on the URL you posted, the connection URI there differs after the port is specified.  It shows something like:
```

jdbc:sqlserver://<host>:<port> ;databaseName=<name>;user=<user>;password=<pass>

```

---

### Post by 1clue on 2016-12-19
The Microsoft Sql Server (mssql) resides on the linux box. Not on a VM.

I know that part is working, I can connect to it from SSMS from another system. This proves the port is open from remote hosts. I think I need to do more research on the jdbc url.

---

### Post by SeijiSensei on 2016-12-19
Any chance you can use ODBC rather than JDBC?  If so, take a look at [unixodbc]("http://www.unixodbc.org/") and see if that helps.

---

