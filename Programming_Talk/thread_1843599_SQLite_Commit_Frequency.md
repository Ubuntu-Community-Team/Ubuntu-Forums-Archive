---
title: "SQLite Commit Frequency"
date: 2011-09-13
forum: Programming Talk
---

### Post by llanitedave on 2011-09-13
I'm building an application in which data is generated during a long series of loops.  The length of the loop is determined by the user, either in specific counts, hours, or indefinitely until halted.  The program is developed in Python, and I'm using the included SQLite3 library to save the data to a separate file.

There are three tables, but the main loop is working in one table with 28 columns defining a single instantiated object.  It can potentially create several thousand object records per loop, or as few as a dozen or so.  The generation times range from about 0.1 second per loop to about 30 seconds depending on the number of objects generated, but these were measured using the objects in lists, without saving them to a database.

I'm sure performance will slow down using the database and saving the records, so I'm trying to decide on the best way to go about it.  My understanding is that all data is held in memory until a 'commit' command is issued, at which point it is written to the file.  The more commits, the slower the operation.  The other consideration is that the data is vulnerable to run-time interruption prior to the commit being done.

I plan on experimenting with different approaches, but I was wondering if anyone already has some ideas or guidance here.  Should I do the commit at the end of every loop?  Should it depend on the amount of data in memory?  Maybe a measured timespan?

What other considerations am I missing?

Thanks in advance for any ideas!

---

### Post by Senesence on 2011-09-13
Large, infrequent commits would make for best performance - I was told this many times.

Your metric should be based on a reasonable unit of storage; it doesn't have to be raw memory (as in bytes), but you could have a commit at every N records.

How large N should actually be depends on various other factors that I'm not all that familiar with, like expire times for transactions, what you can conveniently store in memory, what "commit failure" actually entails, etc.

For example, if commits fail at some frequent rate, and failure requires a new commit attempt, then committing in overly large chunks would be ill advised; you have to recommit that whole massive chunk, which would probably take more time.

---

### Post by llanitedave on 2011-09-13
Thanks, Senesence.  I hadn't heard it put that way before, but it makes good sense.  It looks like I'm just going to have to experiment.

---

### Post by tgalati4 on 2011-09-13
Perhaps a key-value store database would be a better fit for your application than a standard field table.

[http://www.couchbase.org/membase](http://www.couchbase.org/membase)

---

### Post by llanitedave on 2011-09-14
Hmmm.  Looks interesting, but also looks like I'd have to start from scratch.  Not sure what would make it compelling.

---

