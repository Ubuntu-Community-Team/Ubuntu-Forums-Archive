---
title: "Need help choosing the database !!!"
date: 2012-09-27
forum: Programming Talk
---

### Post by vikkyhacks on 2012-09-27
I am developing an application for billing system(in c sharp), i need to have a small database to store the bills and retrieve as and when required. I don wish to go in for any mysql, postgresql kinda dbs where i need to have a client server model ... what other databases u think can i use for this BILLING APPLICATION IN C# .NET

---

### Post by bouncingwilf on 2012-09-27
Assuming your data requirements are reasonably modest (sub TB), then I'd recommend you take a look at Sqlite; Its serverless small and reasonably fast. 


Bouncingwilf

---

### Post by ofnuts on 2012-09-27
> **vikkyhacks said:**
> I am developing an application for billing system(in c sharp), i need to have a small database to store the bills and retrieve as and when required. I don wish to go in for any mysql, postgresql kinda dbs where i need to have a client server model ... what other databases u think can i use for this BILLING APPLICATION IN C# .NET
The big advantage of the canonical server-based DB is that it is easy to have several concurrent uses. And if your application has any future this requirement will show up. This also allows someday to move the DB server to another machine to spread the load, etc...

---

### Post by vikkyhacks on 2012-09-29
i dont need a server/client for model for this simple software which will run in any old p4 with 256gigs of ram and one billing clerk sitting on it, i need any file based system, Is there any other file based system other than SQLite ????

---

### Post by mevun on 2012-09-29
> **vikkyhacks said:**
> i dont need a server/client for model for this simple software which will run in any old p4 with 256gigs of ram and one billing clerk sitting on it, i need any file based system, Is there any other file based system other than SQLite ????

There is berkeley db, but I don't really know how its architecture has changed over the years.  It used to not support SQL statements, but the wiki page says that Oracle corp. now owns the software and added sqlite to it.  Maybe they just added the query parser?

---

### Post by llanitedave on 2012-09-29
What's wrong with sqlite?

---

### Post by vikkyhacks on 2012-09-30
> **llanitedave said:**
> What's wrong with sqlite?

 i am looking for something strongly typed, i don want the datatype to change depending on the inputs that i feed it, like how sqlite has, i need triggers, stored procedures and all the features (at least 60% of what SQL Server, MySQL, Oracle give )

 I just can't digest the fact that only ms access(i hate it and which is M$)and SQLite are the only file based database systems that i can find ...

---

### Post by T.J. on 2012-09-30
> **vikkyhacks said:**
>  I just can't digest the fact that only ms access(i hate it and which is M$)and SQLite are the only file based database systems that i can find ...

The more important question really is do you require ACID  compliant databases? If not, there are all kinds of options, including NoSQL.

Unfortunately, if you are running a flatfile/embedded database on the Windows platform (assuming Windows because of  C#), and thus not using a client/server database - the only two reasonable opensource choices are probably SQLite or Berkeley.  In order to save yourself time and sanity - and have all the features of stored procedures -  I'd resign myself to using a local copy of either SQL Server Express, MySQL, or PostgreSQL.

---

