---
title: "Postgres performance on virtualized server much faster than physical"
date: 2016-10-13
forum: New to Ubuntu
---

### Post by hofmann1234 on 2016-10-13
Hello,
first of all: Sorry for my bad english.

I've got a problem with Ubuntu and Postgres.
First I tried to Install Ubuntu Server 16.04 in VirtualBox with an Windows Host, updated it and it works fine. No changes wore made except for a new postgres user!
Then I tried to install the same way directly/physically on host, all seems to work fine but there is a big problem: Performance.
On the same PC (not identical, same!), the same harddisk, completly new formatted the postgres works really slow. It's somewhere around factor 50. That is completly incomprehensible (/ not understandable) to me. It should work faster or at the same speed as in a virtualized way.

If this would happen for a bit of data it could be caching, but it was testet with ~ 50 Million Insertions with around 500 bytes, and the virtual server had only 1 GByte of ram, the physical has 8 GByte.
I tried another realhost: Even there the speed is really slow. I stopped the insertions after one hour and it has completed only 7% - but on this it was never tested virtually.

I don't have any clue what the problem could be

---

### Post by T.J. on 2016-10-13
> **hofmann1234 said:**
> Hello,
first of all: Sorry for my bad english.

I've got a problem with Ubuntu and Postgres.
First I tried to Install Ubuntu Server 16.04 in VirtualBox with an Windows Host, updated it and it works fine. No changes wore made except for a new postgres user!
Then I tried to install the same way directly/physically on host, all seems to work fine but there is a big problem: Performance.
On the same PC (not identical, same!), the same harddisk, completly new formatted the postgres works really slow. It's somewhere around factor 50. That is completly incomprehensible (/ not understandable) to me. It should work faster or at the same speed as in a virtualized way.

If this would happen for a bit of data it could be caching, but it was testet with ~ 50 Million Insertions with around 500 bytes, and the virtual server had only 1 GByte of ram, the physical has 8 GByte.
I tried another realhost: Even there the speed is really slow. I stopped the insertions after one hour and it has completed only 7% - but on this it was never tested virtually.

I don't have any clue what the problem could be


Any database software - Postgres, MariaDB, or even SQL Server - depends on setup optimizations and the type of file system used.  I humbly suggest that you look there first for the obvious culprit.  What filesystem are you using and what block size?

---

### Post by hofmann1234 on 2016-10-13
Thanks for the fast reply

I haven't changed anything, or set 'special' settings during install:
So it is ext4 and the default block-size.

Well, the size of the partition on the physical installation is greater (no Windows Host which needs some space). The hard-disk is ~ 500 GByte, the virtual drive had 100 GByte(? not really sure, but i think I had set it to 100). If this could be a big impact on performance: Which folder stores the database-files. I could reinstall and make a partition with ~50 GByte only for this folder / these files and test again.
 And which blocksize should be selected? I would tend to 50 MB if possible. In the end there will be less than 150 tables, only a handfull small ones. If I understand the documentation correctly postgres splits tables into 1 GByte parts if the size gets bigger.

But I think that this could not the only reason

---

### Post by SeijiSensei on 2016-10-13
In my experience, the most important feature affecting PostgreSQL performance is whether all the relevant fields are indexed.  Any field that appears in a WHERE clause needs an index.  If you have multiple fields in a WHERE clause you need an index based on all them as well:
```
CREATE INDEX some_index ON some_table (field1, field2, ...);
```

That said I have never seen the symptoms you describe, and I've been using PostgreSQL for two decades now.  Did you create a swap partition when you installed Ubuntu?  With 8 GB of physical memory that shouldn't be an issue.  Are you running other applications on the machine besides Postgres?  What if you stop them all and just use it?  Try opening a terminal window and running "top" while you execute some queries.  What do you see?

You can also use some of the performance checking [tools]("https://www.postgresql.org/docs/9.4/static/performance-tips.html") that come with PostgreSQL, particularly the EXPLAIN command.

---

### Post by T.J. on 2016-10-13
> **hofmann1234 said:**
> Thanks for the fast reply

I haven't changed anything, or set 'special' settings during install:
So it is ext4 and the default block-size.


But I think that this could not the only reason



It isn't but it was a valid question.  Some of the newer filesystems people use are not completely stable.  Have you checked the process load when running your queries?  That will certainly be different in a VM versus native.  You may have another process affecting results.

---

### Post by hofmann1234 on 2016-10-14
Thanks for the replies.

There are no unwanted processes, and the load is less than 0.2 with four cores on the physical - so max shoould be 4 if I am correct.

 I will reinstall both systems parallel on monday, beacause the comparision will be easier then.

---

### Post by SeijiSensei on 2016-10-16
Max load can be enormous.  I've had machines with load averages above 20 when there were serious problems.  0.2 is pretty reasonable depending on what else is running.

---

