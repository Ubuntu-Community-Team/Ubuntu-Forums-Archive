---
title: "What is so special about Oracle"
date: 2007-12-02
forum: Programming Talk
---

### Post by raxz on 2007-12-02
Hi all,

I've been trying to install oracle for school in Ubuntu but I don't think I would having read this [guide]("http://www.dizwell.com/prod/node/1046") and [this guide as well]("http://www.pythian.com/blogs/549/installing-oracle-11g-on-ubuntu-linux-704") I'll probably end up using Windowze so I can use Oracle XE and use J-creator

...well long story short why the heck do I have to [download]("http://www.oracle.com/technology/software/products/database/index.html") aside from it being less hassle/risky I would save some disk space I mean 1.7 GB for a database and allot another 6GB for it? Aside from PL/SQL I see no special feature for this database lang(?)

I sill prefer PSQL and MySQL so I am wondering what does it have that these "free" databse alternatives don't? PL/SQL?

please enlighten me....:popcorn:

---

### Post by Royall on 2007-12-02
I'm not sure about PL/SQL, but I know that for my second database class I used Postgre and enjoyed it more the Oracle. If I were you, I'd just use Postgre.

---

### Post by ankursethi on 2007-12-02
At my school, they teach us SQL using Oracle. At home, I learn it using SQLite.

Oracle : 6 GB
SQLite : 250 KB

SQL is SQL. It's a standard. It will work the same everywhere. If you're just learning SQL, you do not need to worry about the implementation. You will only run into problems if you're learning something that is very Oracle-specific. Anyway, Oracle has no place on a home computer/school lab. It's something you would find in data centers storing terabytes of information.

That said, you should probably wait around for somebody more experienced to reply. I'm not a database person (yet).

---

### Post by aks44 on 2007-12-02
> **raxz said:**
> what does it have that these "free" databse alternatives don't? PL/SQL?
The real question, I guess, is "*why is Oracle the undisputed #1 database vendor when there are equivalent products that are way cheaper, or even free?*".

In a few words: it's the most stable, scalable and efficient database out there. Enterprise-level databases are huge, and they need an engine that can securely yet efficiently cope with their sheer amount of data.

Most small-to-medium applications don't really need this power, but if you plan to write any serious database-based application you'll have to deal with Oracle one day or another.


> **ankursethi said:**
> Anyway, Oracle has no place on a home computer/school lab. It's something you would find in data centers storing terabytes of information.
What's the point of school then if it doesn't prepare you to deal with real-world systems? And no, Oracle isn't limited to such huge data-centers, it is used even in smaller setups (eg. a few gigabytes of business-critical data are enough to justify an Oracle setup).

---

### Post by CptPicard on 2007-12-02
> **aks44 said:**
> eg. a few gigabytes of business-critical data are enough to justify an Oracle setup.

We've got a few gigabytes of business-critical data -- essentially sort of accounting in a bank-style application. You've got to know whose money went where, down to the cent, and no magic disappearance or appearance of money. PostgreSQL works just great; on the other hand I wouldn't trust the MySQL crowd's somewhat cavalier attitude to small things such as ACID compliance and referential integrity.

Soonish we'll have to start thinking about replication in a cluster both for efficiency and data security... we'll see how it goes.

If the school is just about teaching SQL and general database issues, no reason to use Oracle. If you're going to be an Oracle-certified DBA managing genuinely huge amounts of data, it's a different issue.

---

### Post by jflaker on 2007-12-02
Yahoo uses MySQL as their backend storage engine.  A few years ago, MySQL was not a DB of choice for more than the casual user due to limitations of storage.........Today, MySQL will scale to Multiserver server farms and High Availability configurations.......

It is all in what you want, not really capabilities.  Oracle has a support matrix that is great for enterprise, 24/7 support.

---

### Post by pmasiar on 2007-12-02
IMHO MySQL is very good handling databases which use read much more often than write (as websites do), Oracle is more focused on transactions processing.

Big companies prefer to have a vendor to choke if anything goes wrong, Ie if Sarban-Oxley act requires some kind of audit and certification, CEO will pay whatever it takes to keep her out of jail.

Oracle database admin has 150K salary for a reason: Oracle is more powerful and less easy to handle, exactly as semi truck compared with a pickup truck.

"SQL is a SQL" is not true: **every** SQL engine is different, has custom enhancements which you need to avoid (if aiming for database independent app), or exploit (if you have to squeeze last bit of performance).

I am pretty sure that your SQLite is not capable handling huge select query while simultaneously updating same data by 100 different users, and making backup, and synch to remote facility.

---

### Post by raxz on 2007-12-02
I think they just want us to learn SQL and just feel what it's like to make something with a database but I would say MySQL/PSQL would have been less of a hassle...

So Oracle is suited for BIG BIG companies with critical data while the other databases are for small to big companies but are not that good at it?:confused:

[quote=jflaker] 
It is all in what you want, not really capabilities. Oracle has a support matrix that is great for enterprise, 24/7 support.
[/quote]

What is a support matrix?

[quote=pmasiar] 
"SQL is a SQL" is not true: **every** SQL engine is different, has custom enhancements which you need to avoid (if aiming for database independent app), or exploit (if you have to squeeze last bit of performance).
[/quote]

uhm I thought they were....could you give some examples of these "custom enhancements"?

---

### Post by LaRoza on 2007-12-02
> **raxz said:**
> 
uhm I thought they were....could you give some examples of these "custom enhancements"?

There is the SQL specification, and the various apps dialects. The basics are almost always the same.

MySQL, MS SQL Server, Oracle, and all others have features specific to them.

---

### Post by Majorix on 2007-12-02
> What is so special about Oracle

Nothing. Its overrated. And so is MS SQL Server.

---

### Post by pmasiar on 2007-12-02
Market position:

[http://en.wikipedia.org/wiki/Oracle_Database#Competition](http://en.wikipedia.org/wiki/Oracle_Database#Competition)

Differences:

[http://en.wikipedia.org/wiki/Comparison_of_relational_database_management_systems](http://en.wikipedia.org/wiki/Comparison_of_relational_database_management_systems)

---

### Post by raxz on 2007-12-03
LOL should have thought about Wikipedia...

having browsed the Wiki links I can say that I prefer PSQL / MySQL to Oracle then..thanks everyone.

---

