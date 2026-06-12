---
title: "Log to MySQL"
date: 2011-02-10
forum: Programming Talk
---

### Post by nabberuk on 2011-02-10
Hi,

I'm looking to create a simple C program to dump a log file to a MySQL database. This log file is constantly updated.

Whats the best way to handle this?

Open Log File > Insert in to DB > Delete entries that have been inserted

Will i run into issues when an app is trying to write to the log file whilst it's being exported to the database?

Many thanks for any help!
Nathan

---

### Post by Some Penguin on 2011-02-10
A fairly general solution would be to reconfigure your logger to write to a named pipe, and to have a server read the named pipe and multiplex the output to everywhere you want it (a file, a table, et al). If you're using an existing logging framework, it may already support multiple outputs (ala Java's log4j's multiple appenders).

---

### Post by nabberuk on 2011-02-10
I should point out that this log is from dansguardian, so i don't think i'm able to reconfigure logging as a named pipe.

thanks for your reply.
nathan

---

