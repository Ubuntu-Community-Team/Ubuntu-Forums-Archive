---
title: "What's the best database for storing time series data?"
date: 2010-01-16
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-01-16
I am working on an financial project where I want to archive time series information, "tick data".  A ton of data would be archived, probably around 20-50 MB / day per security depending on market activity.  However, SQL is probably a bit overkill.  My average request for backtesting would be to run through an entire history of tick data, fetching one record at a time -- or in groups, but ordered by time from past to present.  So my selection query would be pretty simple, "Give me the history for ticker symbol ES".  I don't need all the selection clauses that SQL supports.  Basically, a serialized map of linked lists would probably work, but I would like the system to have better data protection / failure prevention mechanisms.  I have heard recommendations to use Berkley DB, but that was 3 years ago.  Not sure what's current today.  Database must be free and preferably open-source so I can run it under Linux.  Any ideas?

---

### Post by CptPicard on 2010-01-16
Well, SQLite? SQL might be overkill, but that one is so simple to use that there is no reason IMO not to use it even in less demanding applications (provided it performs fast enough; this is easy to verify with a quick prototype).

Just remember to number your ticks with a running ID and create an index on that so returning the time-series in correct order is fast.

---

### Post by SNYP40A1 on 2010-01-16
I have used SQLLite for other projects and I like it.  I thought about using it -- point I made about SQL being overkill is that, sure, I would love the product to support SQL, but if the database does not need to be relational at the tick level, maybe I can trade that off in exchange more performance -- by using a database that basically looks like a map and linked list.  

What I have realized is that I might as well cross that bridge when I come to it.  Just use good design around the database part so that I can swap it out later when more performance is desired. If space / performance really becomes an issue, I'll have to develop my own database specific to this task.

---

### Post by CptPicard on 2010-01-16
Just using files would also do :)

---

### Post by SNYP40A1 on 2010-01-16
I have also been considering that as well. :-)  Only issue would be what happens if the computer loses power while writing a  binary or text file.  Could it be recovered?

---

### Post by CptPicard on 2010-01-16
Just flush/sync a lot...

---

### Post by Axos on 2010-01-16
Does SQLite give you any more protection against data loss than an ordinary file? Just because something gives you an SQL interface doesn't necessarily mean it has a bullet-proof storage engine with the synchronization necessary to survive power outages intact.

---

### Post by c0mput3r_n3rD on 2010-01-16
PERL (practical extraction and report language) would work well in my opinion.  I dabbled with it but realized I have no real use for it :)  One of the things I found most interesting is that you can call OS commands with it.  So if you wanted to compress/decompress files you can just call linux's uucompress/uuncompress, gzip or what have you to accomplish that.  Same works for creating files or directories, searching with grep and egrep... though if you work too much with the system commands you might as well script it in bash or tcsh.  There are also a lot of good tutorials on the web that are free.  It is quite proficient at searching through files as that's what's basically used for; extracting and reporting.

---

### Post by TheStatsMan on 2010-01-16
Out of curiosity what do you want to do with the data. If you work for a Uni you should already have access to such data sets and I would imagine private enterprise is the same. Is this for a home trading project?

---

### Post by SNYP40A1 on 2010-01-16
> **TheStatsMan said:**
> Out of curiosity what do you want to do with the data. If you work for a Uni you should already have access to such data sets and I would imagine private enterprise is the same. Is this for a home trading project?

Yes, it's a home project.  If you or anyone else has access to such data, I would like to become your friend. :-)

---

### Post by SNYP40A1 on 2010-01-16
> **Axos said:**
> Does SQLite give you any more protection against data loss than an ordinary file? Just because something gives you an SQL interface doesn't necessarily mean it has a bullet-proof storage engine with the synchronization necessary to survive power outages intact.

I assumed that they would have considered robustness to power-fail and other forms of data corruption as part of the design.  Data corruption is a practical issue that any database must deal with to some extent.  Most handle this by locking the commits.  As far as data recovery due to file corruption, not sure what can be done there.

EDIT: I just checked wikipedia:

[http://en.wikipedia.org/wiki/Comparison_of_relational_database_management_systems](http://en.wikipedia.org/wiki/Comparison_of_relational_database_management_systems)

Yes, most databases do offer ACID: [http://en.wikipedia.org/wiki/ACID](http://en.wikipedia.org/wiki/ACID)

---

### Post by TheStatsMan on 2010-01-16
> **SNYP40A1 said:**
> Yes, it's a home project.  If you or anyone else has access to such data, I would like to become your friend. :-)

Well, I could get such data, with a lot of effort (I work in a maths department not the business department), but even if it was easy for me to get there is no way I would give out such data as it could get me into serious trouble. I am quite well paid and I like my job so I would like to keep it.  :) 

Is this for technical trading or are you going to apply "proper" statistical models for time series. If it is the latter it isn't easy, particularly if it is in real time, unless you are using the data set to construct realised volatility (options trading?). At a tick by tick level you will have to account for microstructure effects in the data. 

I realise if this is a trading strategy you can't provide any specific information, but I am curious to what direction you are taking?

---

### Post by SNYP40A1 on 2010-01-16
> **TheStatsMan said:**
> Well, I could get such data, with a lot of effort (I work in a maths department not the business department), but even if it was easy for me to get there is no way I would give out such data as it could get me into serious trouble. I am quite well paid and I like my job so I would like to keep it.  :) 

Is this for technical trading or are you going to apply "proper" statistical models for time series. If it is the latter it isn't easy, particularly if it is in real time, unless you are using the data set to construct realised volatility (options trading?). At a tick by tick level you will have to account for microstructure effects in the data. 

I realise if this is a trading strategy you can't provide any specific information, but I am curious to what direction you are taking?

I have been reading through some trading forums and came up with some ideas.  I want to apply them to past data and see if they yield any insight.  Unfortunately, full book past data is very expensive (at least since OpenTick went away).  I still have a lot of other development to do, but I want to start collecting data now and build up a database so that it's ready when I need it.

---

### Post by Axos on 2010-01-17
> **SNYP40A1 said:**
> I assumed that they would have considered robustness to power-fail and other forms of data corruption as part of the design.
I should have done some homework before posting! I see now that SQLite is quite robust:

[http://www.sqlite.org/transactional.html](http://www.sqlite.org/transactional.html)

I was basing my hunch on past experience with a low-end commercial database which had no such robustness (no doubt to ensure it didn't compete with the same company's high-end product).

---

### Post by CptPicard on 2010-01-17
> **SNYP40A1 said:**
> I assumed that they would have considered robustness to power-fail and other forms of data corruption as part of the design. 

Well, all half-decent databases keep integrity in case of power-fail, but absolute maintenance of "everything being on drive that has to be there" is actually quite hard. Data loss is always a possibility unless you have an UPS. 

However, in this case, if you just have a simple file, flushing it to disk after every write (which certainly gives you a performance hit) should give you a decent enough outcome. "Corruption" is not really a problem, the tail end last record of the file being potentially "corrupt" won't kill your data.

This is how I handle the rather important task of "keeping track of what has been sent" in my multithreaded bet-submitting program we use running Finland's biggest sports betting operation... some 60 M€ worth submitted without error so far, so the simple strategy should work for you too ;)

> **SNYP40A1 said:**
> I still have a lot of other development to do, but I want to start collecting data now and build up a database so that it's ready when I need it.

I'm curious as to how your project is going. :) As we discussed before, I've done some analysis on daily data as well... but as it turns out, the more you stare at the graphs, the more it trains your wetware neural network... I have pretty much become a "manual" trader recently because I perform better myself than any computerized strategy (that I can think of) :p

---

### Post by tom66 on 2010-01-17
I would recommend SQLite3 over any other server based database for this use case. I wrote a small benchmark between MySQL and SQLite3. SQLite3 won out in all tests except for the create table/add column/drop table/rename table/create index tests, but they aren't common operations, so I don't think that is a problem. In most tests it was much faster on SELECT and UPDATE than MySQL. INSERT was just about the same speed.

---

### Post by CptPicard on 2010-01-17
That's not surprising, considering that SQLite operates on a file in the same process, while for MySQL you need to go through all the machinery of a full-blown client/server model...

---

### Post by SNYP40A1 on 2010-01-24
> **tom66 said:**
> I would recommend SQLite3 over any other server based database for this use case. I wrote a small benchmark between MySQL and SQLite3. SQLite3 won out in all tests except for the create table/add column/drop table/rename table/create index tests, but they aren't common operations, so I don't think that is a problem. In most tests it was much faster on SELECT and UPDATE than MySQL. INSERT was just about the same speed.

Is MySQL generally considered to be a fast database relative to competition (PostGRESQL)?  I've seen conflicting benchmarks benching SQLLite vs. other databases.

> I'm curious as to how your project is going. As we discussed before, I've done some analysis on daily data as well... but as it turns out, the more you stare at the graphs, the more it trains your wetware neural network... I have pretty much become a "manual" trader recently because I perform better myself than any computerized strategy (that I can think of) 

You are probably right...in any case, I still need the data.  Some things are very hard to chart directly, hence the purpose for this post: [http://ubuntuforums.org/showthread.php?t=1387984](http://ubuntuforums.org/showthread.php?t=1387984).

> That's not surprising, considering that SQLite operates on a file in the same process, while for MySQL you need to go through all the machinery of a full-blown client/server model...

That's what I was thinking too...SQL is over-kill for my use case.  Storing the data in a compressed binary format, one file per day, and using folders to separate exchange/symbol sounds like the best approach at the moment.  Also makes copying/backup the data easier too.

---

### Post by Gumshoes on 2011-01-03
I am curious to know what solution you ended up using.  I am currently experimenting with using Postgresql 9 to store billions of time series values.  Some early findings that may be of interest.

Using the following table with indexes on date, quality, and tag_id I can get ~10000 values inserted/sec if you group the inserts into groups of 10000 or more.  The DB server is a middle of the road HP BL class blade.

```
CREATE TABLE "values"
(
  date date,
  "time" time without time zone,
  val double precision,
  quality smallint,
  tag_id integer,
  CONSTRAINT tag_id_fk FOREIGN KEY (tag_id)
      REFERENCES tags (id) MATCH SIMPLE
      ON UPDATE NO ACTION ON DELETE NO ACTION
)
WITH (
  OIDS=FALSE
);
```

What kills performance over time is the indexes, once you get a few million records inserted the insert rate slows due to the additional overhead of updating and writing the indexes to disk.  Turn off the indexes and the insert rate remains steady but then your queries will all result in full table scans and take longer with every extra row.

Another issue is SQL has no quick way (that I know of) of getting the last inserted value for a point.  Your schema would have to have another table that records the first and last time of very point.

I think that with a well designed schema and a beefy DB server a timeseries DB of a few billion points is doable but beyond that something else is required.  If you don't need the relational features of a relational DB then for sure binary files containing ordered timeseries data will be faster.  It seems that all the big trading firms store and analyze timeseries data using specialized, non-relational, DBs such as [http://kx.com/](http://kx.com/).

---

