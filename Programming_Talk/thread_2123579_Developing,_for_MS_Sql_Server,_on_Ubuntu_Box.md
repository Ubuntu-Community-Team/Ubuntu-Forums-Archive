---
title: "Developing, for MS Sql Server, on Ubuntu Box"
date: 2013-03-08
forum: Programming Talk
---

### Post by Noble Bell on 2013-03-08
I am in the process, 4 months now, of switching over to Ubuntu Linux after 25+ years with MS. I work with Java and Python using Eclipse. A question that has often crossed my mind but have been unable to think of a reasonable solution is this...

If I wanted to write a piece of software for general public use or write a piece of software for a client that had a requirement of working with a MS Sql Server database how would be the best way to go about doing this without having to develop this software on a Windows desktop with Sql Server Express installed?

Thoughts?

TIA
Noble

---

### Post by SeijiSensei on 2013-03-08
Some languages like PHP have [built-in functions]("http://php.net/manual/en/book.mssql.php") to use MS-SQL.  I don't use Python, but there might be the equivalent functions there.  If not, see if there are any ODBC functions available.  Otherwise you can try using [unixODBC]("http://www.unixodbc.org/") to communicate with the SQL server.

If you are writing an application from the ground up and can choose any database, I'd go with [PostgreSQL]("http://www.postgresql.org/").

---

### Post by slickymaster on 2013-03-08
+1 on [COLOR=#000000]SeijiSensei's advices.[/COLOR]

> **SeijiSensei said:**
> Otherwise you can try using [unixODBC]("http://www.unixodbc.org/") to communicate with the SQL server.

There's also [SQuirreL SQL]("http://www.squirrelsql.org/"), which basically is a graphical Java program that will allow you to view the structure of a JDBC compliant database, browse the data in tables, issue SQL commands, etc.

> **SeijiSensei said:**
> If you are writing an application from the ground up and can choose any database, I'd go with [PostgreSQL]("http://www.postgresql.org/").

Myself, I prefer [MySQL]("http://www.mysql.com"), but that's just a personal preference.

---

### Post by Noble Bell on 2013-03-08
I will check into this stuff. Thanks.

---

### Post by SeijiSensei on 2013-03-08
> **slickymaster said:**
> Myself, I prefer [MySQL]("http://www.mysql.com"), but that's just a personal preference.

PostgreSQL is a lot [closer]("http://www.theregister.co.uk/2011/09/12/postgresql_9_1_cloud_server/") to "enterprise" databases like Oracle and MS-SQL than is MySQL.

---

### Post by Some Penguin on 2013-03-09
It'd actually fairly problematic because SQL implementations tend to not perfectly follow SQL standards, and the standards are not entirely comprehensive, so building and testing against e.g. PostgreSQL or MySQL may not prove anything about how your SQL will actually be handled on MS SQL Server.   But hey, if you're writing for a client, you may not have any choice about the matter short of dropping the contract...

To reduce the amount of pain, you'd probably want to

1) isolate EVERYTHING specific to the DBMS to the internals of a data access object (DAO), which basically /only/ handles DBMS logic and doesn't do anything DBMS-specific in the API,
2) have all application logic communicate only through that DAO
3) have the DAO be an interface, and 
4) have specific implementations of the DAO for particular DBMSs which have valid SQL for the particular required dialect.  The choice of JDBC driver would be specified via a string, and you might be able to get away with the same set of basic operations but with SQL tailored for either.

In such a case it might be worth looking at something like [http://www.jooq.org](http://www.jooq.org) -- SQL-generating stuff so that you can write less DBMS-specific code, since that way you wouldn't be relying on hoping for correctness regarding an implementation you might not actually be able to test without the given DBMS.

Oh, and of course stay the heck away from things like PL/pgsql or other utterly non-portable things.  Doing this also makes it easier to be burned by quirky performance differences since the DBMSes may not be equally good at the same operations... but at least it'll make it possible to test your application logic against whatever DBMS you happen to use, and isolate the DBMS-specific differences to one layer.

---

### Post by r-senior on 2013-03-09
All good advice from SomePenguin. Assuming your database access is in Java (that could be a false assumption), you could also go one step further and use an ORM tool like Hibernate, which will generate all the SQL code based on object to relational mappings. Switching dialect is just a setting in the config file. This should be a very reliable way of flipping the underlying database implementation because Hibernate is dealing with it.

I've not done this with SQL Server, but I have freely switched between MySQL, Oracle and DB2 so I've no reason to believe SQL Server would cause problems.

---

### Post by SeijiSensei on 2013-03-09
I didn't think the OP needed help with the SQL code, just with inter-connectivity between a client program written in a platform-independent language like Python running on Ubuntu and the MS-SQL server.

---

### Post by slickymaster on 2013-03-11
> **SeijiSensei said:**
> PostgreSQL is a lot [closer]("http://www.theregister.co.uk/2011/09/12/postgresql_9_1_cloud_server/") to "enterprise" databases like Oracle and MS-SQL than is MySQL.

No argues there, I was just stating a personal preference.

There's that description:
> MySQL is what you get when application developers build an RDBMS.
PostgreSQL is what you get when database developers build an application development platform.
And it's probably an accurate one, since I'm mostly an application developer, not a database one.

---

### Post by slickymaster on 2013-03-11
> **SeijiSensei said:**
> I didn't think the OP needed help with the SQL code, just with inter-connectivity between a client program written in a platform-independent language like Python running on Ubuntu and the MS-SQL server.

+1
That was also my impression.

---

### Post by r-senior on 2013-03-11
I'm sure the OP didn't need help with the SQL, but the point is that SQL can differ between databases. Auto-generated primary keys for example. Interposing a layer that can handle or encapsulate that has to be a good idea doesn't it?

---

### Post by slickymaster on 2013-03-11
> **r-senior said:**
> I'm sure the OP didn't need help with the SQL, but the point is that SQL can differ between databases. Auto-generated primary keys for example. Interposing a layer that can handle or encapsulate that has to be a good idea doesn't it?

Completly right. Of course it's a good idea.

Since english is not my native language, I could have misunderstood the OP original intention.

---

