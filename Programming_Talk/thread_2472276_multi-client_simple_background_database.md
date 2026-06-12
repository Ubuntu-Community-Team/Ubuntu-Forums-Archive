---
title: "multi-client simple background database"
date: 2022-02-22
forum: Programming Talk
---

### Post by Skaperen on 2022-02-22
i have a need to create an app that will access a database of simple key-value settings.  there will be no SQL so i'm looking for some NO-SQL solution.  but this app is a little different.  many instances of it will be launched at random times, all under one common non-root userid.  when no instances are running there needs to be no background processes running.  to avoid data corruption, they all need to use a common data server.  if there is no server running, he first to discover there is no server needs to start one.  when all clients disconnect and all data is written from buffers, it must exit.

what is a good database system to do this under either C or Python?  Python is preferred.  coding for this has not started, yet.

---

### Post by TheFu on 2022-02-23
It has been a few years since I touched nosql DBs.

I've used C-tree, a commercial product.  This is an embedded DB with C-hooks. If there are more than a few processes locking the DB file, it was possible for the DB to become locked. I remember being shocked at how cheap the cost was at the time after being used to spending $100K+ on stuff.

I've also used Raima DB, a much more expensive solution, but multi-user access never entered a deadlock. Also, all records are the exact same length, so jumping from record to record was very fast integer math (internally).  1 file = 1 table, but we did mix object types in the same files, if their max record length was similar. 

A simple oref type was used.  {type}-{seq} ... was the logical way to think of it. Both were 16-bit numbers ... or were they 32-bit?  I don't recall.  We reserved both numbers below 10,000 for our needs. User created records began at 10001 both for the type and seq parts. Pretty standard stuff.

If you just have a few users and only need minimal DB locking capabilities, then I'd use sqlite.  There are plenty of connection libraries, ORMs if you like, that will completely hide any SQL.  I know Perl DBXi can.  And if an install outgrows sqlite, there are 10 other DBMS that a config file change will make work thanks to DBIx.

Google says that there is a Python wrapper for perl DBIx. I didn't look any further.

If no locking is required, perl has the suite of "Tie" classes which can convert nearly any text file into a DB. I'd be surprised if python didn't have something similar.  If you need weenie locking, implementing a very simple flock() should be easy in any language - or just use flock like we do in bash scripting.

---

