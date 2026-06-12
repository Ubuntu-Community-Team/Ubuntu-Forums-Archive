---
title: "In-RAM database?"
date: 2009-01-03
forum: Programming Talk
---

### Post by CptPicard on 2009-01-03
Something I started thinking about tonight... this has to do with the same system that I wrote the Java vs. C++ thread about. :)

Now, anyone who read the thread must have noticed that in the actual number-crunching code there are very tight inner loop sections that allow the computation of the analysis of millions of records to be performed only if access to individual records is made as quick as possible. So far so good.

These days the input for the analysis tool comes from a text file, which is scraped together from a web page by concurrent http  request threads, so we end up for example with a 3^13 row input file. This works, but the workflow is a bit too linear and as a whole the whole cycle from getting data to doing analysis can take as much as 1-1½ hours.

So I thought of replacing the text file with some sort of database that the analysis tool could read in a version of (the *really* fast access only is needed while actually computing), then push back results, all the while there are threads doing the data gathering  -- and the results from analysis tool can be used to prioritize what data is refreshed first, as the analysis tool gets a good idea of what is interesting and what is not.

Now, I can't do this in the actual analyzer data structure as I can't afford locking or anything like that; any added complication there is "too much" as any extra load adds up as was amply demonstrated by the tree/hash difference in the C++ implementation.

On the other hand a disk database is probably too slow for selecting/updating all 2-10 million rows for an analyzer pass. So an in-RAM database might be nice, and I could even set up a dedicated box for running it. However, I am not quite sure how wasteful in-RAM DBs are in terms of their RAM consumption... any ideas or experiences? :)

---

### Post by |{urse on 2009-01-03
[www.codefarms.com/publications/papers/Resident.pdf <--- you'll need to c&p this manually]("http://ubuntuforums.org/www.codefarms.com/publications/papers/Resident.pdf")

ugh a .pdf but it has a lot of information and C code samples to get you going.

---

### Post by Cracauer on 2009-01-03
For pretty much with any project I ever worked on (all large data) I implemented something to mlock(2) the data into RAM.

I never found this to be an overall advantage. The VM system's choice about what to drop when seems to be pretty highly developed, both on Linux and FreeBSD.

The only specific problem I had is that Linux favors keeping in dirty pages over readonly droppable pages too much (of course it need to do that, but it is overdoing, or was overdoing it). But this mostly went away over the years and large-memory machines now seem to work fine.  Dunno whether that's a change in the kernel code or in the data/heap/memory relationship.

In a word: I would just stuff in more RAM and let the OS take care of it.

I have a commandline utility that you can use to lock a file on disk into memory (also displays how much currently is in memory etc.).  Let me know if you can use that.

---

### Post by CptPicard on 2009-01-03
Well actually, I guess as first thing I will just see how far I can push something like SQLite and whether "one huge table" has any significant overhead... :) being able to network to it from analyzer / data gatherers would be sweet though.

---

### Post by pmasiar on 2009-01-03
Every decent database engine should be able to use in-memory tables, MySQL can:
[http://dev.mysql.com/doc/refman/5.0/en/memory-storage-engine.html](http://dev.mysql.com/doc/refman/5.0/en/memory-storage-engine.html)
[http://en.wikipedia.org/wiki/MySQL_Cluster](http://en.wikipedia.org/wiki/MySQL_Cluster)

---

### Post by pp. on 2009-01-04
It might also be worthwile to differentiate between the database or table at large and the rows you are about to process. 

The rows you are about to process usually are part of a query. Database software is "aware" of the fact that queried rows are about to be fetched and read, and I presume that there are caching techniques present in the database software. Look for "query", "cursor" and, of course, "cache".

---

### Post by Cracauer on 2009-01-04
> **pmasiar said:**
> Every decent database engine should be able to use in-memory tables, MySQL can:
[http://dev.mysql.com/doc/refman/5.0/en/memory-storage-engine.html](http://dev.mysql.com/doc/refman/5.0/en/memory-storage-engine.html)
[http://en.wikipedia.org/wiki/MySQL_Cluster](http://en.wikipedia.org/wiki/MySQL_Cluster)

It really doesn't make a difference whether you work on data that is mapped (or was read) from a file on disk, or whether you work on tables in a malloc()/anonymously mapped area.

Both are subject to being paged in and out by the VM system under the same conditions (except of course readonly mapped pages are dropped earlier).

That's another reason why I recommend not playing with this too much.  In the end, all you might get out of doing this stunt is 1) more complicated code 2) the overhead of copying first and 3) no difference in performance.

If you have enough RAM, you'll live off the database in RAM. If not, you won't. None of these stupid tricks change anything about it.

If you really want to guarantee from-RAM, you can use mlock(2) as I previously indicated but be warned that doing that (as I said I did it for most projects I ever did) has never turned out to be an overall advantage so far, when measuring the whole system for a day or so.

If you decide to mlock(2), it doesn't matter whether you lock the file on disk or some memory region. On the contrary, I find it more workable to lock the files on disk because that way you can write an external program and don't have to screw up your application's code.

---

### Post by pmasiar on 2009-01-04
> **Cracauer said:**
> It really doesn't make a difference 

The difference as I see it is being to able to use SQL to find relevant data, or using other ways. It also depend on what kind of data access (SQL or not) you use for other data.

---

### Post by WitchCraft on 2009-01-04
All I would gonna do is checking the available RAM, and then loading the data (or part of it) from disk to memory, if that is possible. 

You usually need different algorithms when working in RAM, as when you work from disk...
So I'd go to wikipedia and compare performance for the algorithms you need to have, for example sorting.

What you need to look for is the memory consumption of algorithms used, and the best/worst/average speed of the algorithm, and especially its numeric stability...

Also it depends on what database you use.
Some databases are optimized for speed, some for size of the data on disk, and others for maximum features...
Also, you need to look what type of database you use, for example using MySQL, you need InnoDB for the database to be really fast...

If you use PostGre SQL, the data is (by default) compressed, and gets decompressed only on demand (takes time - performance!)

For example if you compare sorting algorithms
[http://en.wikipedia.org/wiki/Sorting_algorithm](http://en.wikipedia.org/wiki/Sorting_algorithm)

mergesort and binary tree sort are the clear winners.
Of course you need to take care when implementing them.

A recursive version of mergesort would certainly crash your system when you have low ram, while an iterative version would be fast as hell.

In other words, I recommend writing your own database, optimized for your needs. You probably cannot have it any faster than that.

If you decide to use an existing database, there's only one recommodation I can give you regarding performance: RTFM !

---

### Post by jmartrican on 2009-01-04
WitchCraft,

Does the compressing of data by postgres also affect writes?  I assume it does but figure I'd ask.  Any way to turn it off in an effort to improve writing?

---

### Post by slavik on 2009-01-04
as long as the compression/decompression calculations are faster than reading the data, you win.

---

### Post by Cracauer on 2009-01-05
> **slavik said:**
> as long as the compression/decompression calculations are faster than reading the data, you win.

But the database will usually not be able to make an educated decision about which blocks will actually hit the disk. Obviously you lose if you have compression in a layer that might be between the application and any kind of buffer cache.

Also, compression (usually) has a larger granularity than disk blocks.

Just because zcat is faster than cat for an unbuffered file doesn't mean that a compressed storage system will be faster (and compression is usually slower than uncompression).

---

### Post by stevescripts on 2009-01-05
> **CptPicard said:**
> Well actually, I guess as first thing I will just see how far I can push something like SQLite and whether "one huge table" has any significant overhead... :) being able to network to it from analyzer / data gatherers would be sweet though.

Cpt Picard - Had I viewed your original post in a timely manner, I would have suggested starting with SQLite, and see how far it gets you...

Being late, I am curious what sort of results you get with SQLite.

Steve

---

### Post by slavik on 2009-01-05
> **Cracauer said:**
> But the database will usually not be able to make an educated decision about which blocks will actually hit the disk. Obviously you lose if you have compression in a layer that might be between the application and any kind of buffer cache.

Also, compression (usually) has a larger granularity than disk blocks.

Just because zcat is faster than cat for an unbuffered file doesn't mean that a compressed storage system will be faster (and compression is usually slower than uncompression).
Even with uncompressed data it can become difficult in figuring out where a record on disk is, that's why there is something called indexing ;)

---

### Post by Cracauer on 2009-01-05
> **slavik said:**
> Even with uncompressed data it can become difficult in figuring out where a record on disk is, that's why there is something called indexing ;)

Uh? Who was talking about the "where"? :confused:

---

### Post by WitchCraft on 2009-01-06
> **jmartrican said:**
> WitchCraft,

Does the compressing of data by postgres also affect writes?  I assume it does but figure I'd ask.  Any way to turn it off in an effort to improve writing?

I don't know actually, but my guess is 'YES'.
Anyway as said above, as long as compression/decompression time lost is <= time won by compressed reading/writing, than it is good, else not.

I know you can turn it off, but you need to go to a postgre forum for details, I'm not an expert at databases. 

Anyway, I'd suggest either using SQlite, if you don't want/have time for writing your own algorithms.
If you have engough time, choose own algorithm, because then you will learn something, else use SQlite.

It would also be interesting to do both, and then compare which is faster ;-)

---

### Post by CptPicard on 2009-01-06
Well, it's not the time to start doing anything on this front yet... I need to get probably the C version of the benchmarking thread into actual usage, and then write Python bindings for the C code (this is one of the reasons why I really like the idea of using C). 

As an aside over the PostgreSQL issue, I am otherwise a huge fan of that particular database, but some operations on it are rather slow...

```

stocks=> select count(*) from stockdata;
  count
----------
 20515399
(1 row)

stocks=> explain analyze select * from stockdata;
                                                          QUERY PLAN
-------------------------------------------------------------------------------------------------------------------------------
 Seq Scan on stockdata  (cost=0.00..652678.00 rows=20515400 width=63) (actual time=7918.153..144306.619 rows=20515399 loops=1)
 Total runtime: 183456.539 ms
(2 rows)


```

Same box I run the benchmarking thread stuff on.

---

### Post by WitchCraft on 2009-01-16
> **CptPicard said:**
> 
As an aside over the PostgreSQL issue, I am otherwise a huge fan of that particular database, but some operations on it are rather slow...


Me too (I very much like stored procedures), but you always need to keep an eye on the speed affecting settings...

---

