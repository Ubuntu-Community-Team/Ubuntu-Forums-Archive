---
title: "Concurrent IO and databases"
date: 2010-09-27
forum: Programming Talk
---

### Post by dv3500ea on 2010-09-27
What is the best way to allow for concurrency with databases and general input/output? How do you safeguard against different processes or threads trying to write different values to the same file or the same place in a database?

I can only seem to get my head around concurrency if I don't use any shared values or IO at all, but if a program is heavily based on a database, I don't know how you would prevent concurrency problems.

---

### Post by Bachstelze on 2010-09-27
There are a lot of mechanisms you can use to prevent such things (locks, semaphores...).  It all depends on the language, though I guess you could find libraries implementing them in most languages.

[http://en.wikipedia.org/wiki/Mutex](http://en.wikipedia.org/wiki/Mutex)

---

### Post by worksofcraft on 2010-09-27
Check the documentation for your database. In MySQL, a database system that is very popular with web applications programmed in php, they use "LOCK TABLES" and you can lock them for read access or read/write access.

This is absolutely essential to maintain consistency of the records in the database when many people could be accessing it online, but also locking it for too long can cause annoying delays for other users.

---

### Post by Some Penguin on 2010-09-27
Look up [ACID]("http://en.wikipedia.org/wiki/ACID").

For MySQL, use the InnoDB engine rather than the default MyISAM.  InnoDB actually attempts to have vaguely reasonable lock behavior.  And frequent use of 'LOCK TABLES' is a sign that you're almost certainly doing it very, very, very wrong.

PostgreSQL handles concurrency *very* nicely.   Turn off autocommit and use explicit BEGIN/END when you want.   It's not too bad at all.  Implementing an INSERT OR UPDATE is slightly fiddly (you can do INSERT - catch primary key violation and UPDATE, you can turn off autocommits, do a select, and use the cursor  to insert, there are other ways as well, it's just not buit in.)

---

### Post by worseisworser on 2010-09-27
> **dv3500ea said:**
> What is the best way to allow for concurrency with databases and general input/output? How do you safeguard against different processes or threads trying to write different values to the same file or the same place in a database?

I can only seem to get my head around concurrency if I don't use any shared values or IO at all, but if a program is heavily based on a database, I don't know how you would prevent concurrency problems.

People often use mutual-exclusion (mutex) or locking, but this often (except in trivial cases) creates or reveals another even greater problem; operations cannot be composed.

A solution to that is STM:
  [http://en.wikipedia.org/wiki/Software_transactional_memory](http://en.wikipedia.org/wiki/Software_transactional_memory)

For I/O in combination with STM one often use an "on commit" type construct which will only be executed when a transaction finishes in completion.


edit: ..i removed the examples because they where probably confusing anyway; perhaps you can post some CLI code that illustrates the problem from your end? in turn, i'll try to explain how i'd solve the problem using STM (if appropriate)

---

