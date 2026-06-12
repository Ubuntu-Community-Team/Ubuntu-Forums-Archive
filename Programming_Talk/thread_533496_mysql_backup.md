---
title: "mysql backup"
date: 2007-08-24
forum: Programming Talk
---

### Post by munichlinux on 2007-08-24
hi,

       I want to take a automatic incremental mysql backup whenever there
is a insert or update happening to the database but i dont like to
schedule the process(something like every hour or day). I cant do replication because i have only one slice. Is there any
tool or script through which i can achieve this?

--
regards,

Prashanth

---

### Post by sacherjj on 2007-08-24
If you must do it with each insert or update, without replication, the only thing I can think of is something that is setup as a trigger on every table talking to another db where the data is stored.

---

