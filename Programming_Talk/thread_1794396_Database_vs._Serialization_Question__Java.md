---
title: "Database vs. Serialization Question : Java"
date: 2011-06-30
forum: Programming Talk
---

### Post by Kentucky88 on 2011-06-30
I want to store time series data.  The time series will only be accessed sequentially.  I actually plan to load it into memory then do some analysis in Java.  My question is, is it better to store the series as an array and then encode the array into a blob and store the blob into a DB or should I store the data in a non-RDBMS?  My intuition tells me that serializing the array into binary and storing the binary blob into a database would be the fastest / most efficient approach since the data will only be accessed serially.  Each object that I am storing is very simple, just a collection of 4 doubles.

Also, can someone recommend a pure Java database to use for this?  My first attempt was ObjectDB, but it really slowed down to a crawl at around 500 MBs in size.  I suspect it was storing each index of the time series array as a separate entry in the database.  I'd really like a very simple 100% Java implementation.  I'm almost to the point of serializing the data into individual files, one per series.

---

### Post by myrtle1908 on 2011-07-01
From memory Apache Derby is a Java db.  Small footprint, can embed.

[http://db.apache.org/derby/](http://db.apache.org/derby/)

---

### Post by megabytemonster on 2011-07-01
I recommend the H2 Database rather than Apache Derby: [http://www.h2database.com/html/main.html](http://www.h2database.com/html/main.html)

I made a program initially using Apache Derby, but moved away from it to H2. H2 also has clearer documentation in my opinion.

---

