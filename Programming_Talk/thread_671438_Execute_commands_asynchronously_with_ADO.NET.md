---
title: "Execute commands asynchronously with ADO.NET"
date: 2008-01-18
forum: Programming Talk
---

### Post by cwaldbieser on 2008-01-18
I have a program that executes commands on a database that sometimes take a long time to complete (for example, deleting many rows).  The program becomes unresponsive during this time because it blocks until the I/O operation is complete.

In an older program, I was able to use the asynchronous methods of ADO to keep the GUI responsive while the data loaded in the background.  I thought that ADO.NET might offer ome kind of similar functionality.

From what I have read, it seems like the API for working with ADO.NET asynchronously exists, but there is a catch.  I have been using the IDbCommand interface and the factory pattern to keep the code that determines the type of database isolated.  However, the methods that start and stop the asynchronous commands (e.g. BeginExecuteNonQuery(), EndExecuteNonQuery()) seem to be defined on the concrete types rather than on interfaces.

Has anyone else run into this problem?  How did you handle it?

---

### Post by DrMega on 2008-01-18
Can you not send it off to a new worker thread, and have that thread raise an event when processing has finished so that the main thread can then pick up the results?

---

### Post by cwaldbieser on 2008-01-21
> **DrMega said:**
> Can you not send it off to a new worker thread, and have that thread raise an event when processing has finished so that the main thread can then pick up the results?

I tried that approach, but that creates a new problem.  The user can cancel the operation and exit the program, but because the thread is still alive, the program won't exit until the I/O operation was completed.  Calling Thread.Abort() doesn't seem to help.

---

