---
title: "Fast non-relational open-source concurrent database?"
date: 2010-07-06
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-07-06
I am currently logging data into binary files.  It's time series data that I want to access sequentially.  The issue is that the data does not arrive in time order, but actually arrives slightly out of order sometimes, usually by a few ms.  It is time-stamped so I can sort upon retrieval.  What I would like to do is not only record this data, but also make it available to other computer(s) on my local network.  I would like to query the server and ask it to retrieve data by time range and product name (so I don't really need the full relational database query power and overhead).  I am currently looking at HDF5, but I have a feeling it might be a pain to get it to work as a server process...I think I would have to do all the socket / server programming myself.  MySQL could work for me.  I could log all my data into MYSql during the week and then dump it into binary files or Berkley DB on the weekend to prevent the tables from becoming too big (I log about 2 GB of data / week).  Performance would not be an issue at this point, but if there's a better solution for what I need, probably worth asking the question now.  I'd need single-writer multiple reader concurrent access too...

---

### Post by cb951303 on 2010-07-06
[http://couchdb.apache.org/](http://couchdb.apache.org/)
[http://code.google.com/p/redis/](http://code.google.com/p/redis/)
[http://cassandra.apache.org/](http://cassandra.apache.org/)
[http://www.mongodb.org/](http://www.mongodb.org/)
[http://1978th.net/tokyocabinet/](http://1978th.net/tokyocabinet/)

---

### Post by SNYP40A1 on 2010-07-06
Thanks, those are good choices, it looks like redis might be closest to what I am looking for.  I basically want to setup a master database where I save all incoming data into database or text file and then replicate the data to one or at most two slave systems.  But after synchronization, when new data comes into the slave system from the master, how can I notify my applications that are processing the data on the slave system about the new data?  When the db is updated with new data, is there a way to setup a process to deliver the only the new data to my apps?  I'm wondering if I have to code up a listener process to do this or if something already exists that I can use.

As far as the data that I am storing, it's just 1 Date-Timestamp, 2 doubles, an integer, and a string (which could be an enum type taking 1 of 5 possible values).  However, there will be a few million of these entries per day.  But I don't need any fancy SQL processing, just a sorted (preferably sorted) up-to-date list of these entries distributed to a slave system is all I need.

---

