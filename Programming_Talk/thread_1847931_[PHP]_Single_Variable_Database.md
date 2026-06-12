---
title: "[PHP] Single Variable Database"
date: 2011-09-21
forum: Programming Talk
---

### Post by ki4jgt on 2011-09-21
Is there a database server which will allow me to keep items as variables instead of installing the huge tables and such involved with MySQL?

---

### Post by cgroza on 2011-09-21
You mean in the following format?
```

var1 = "spam", 1
otherVar = "otherspam", 21312

```
If so a text file parsed into a associative array seems what you need.

---

### Post by ki4jgt on 2011-09-21
A text file doesn't provide the speed I need :-(

---

### Post by Barrucadu on 2011-09-21
Try SQLite, it's pretty simple. It's a full SQL database, but very small compared to a full database server such as MySQL.

---

### Post by johnl on 2011-09-21
You could also use **redis**, which has php bindings, for example [predis](https://github.com/nrk/predis/), which doesn't require any SQL or schema.

---

### Post by Tony Flury on 2011-09-22
Deleted - sorry - thought the OP wanted a python solution - oonly just noticed the PHP tag.

---

### Post by SeijiSensei on 2011-09-22
> **ki4jgt said:**
> A text file doesn't provide the speed I need :-(

I find that hard to believe unless we're talking about a file with hundreds of thousands of lines.  For performance, you can write the file to /dev/shm at startup and take snapshots to disk periodically.

If you use sessions, you'd only need to read the file once per session.  Read the file, parse it into associative arrays, and stash the arrays in the session.

If you only need key/value pairs, you can use [dbm]("http://www.php.net/manual/en/intro.dba.php").

---

### Post by ki4jgt on 2011-09-22
> **SeijiSensei said:**
> I find that hard to believe unless we're talking about a file with hundreds of thousands of lines.  For performance, you can write the file to /dev/shm at startup and take snapshots to disk periodically.

If you use sessions, you'd only need to read the file once per session.  Read the file, parse it into associative arrays, and stash the arrays in the session.

If you only need key/value pairs, you can use [dbm]("http://www.php.net/manual/en/intro.dba.php").

I need to be able to keep a single (changing) variable with traffic that varies from 4 - 1000 users per minute. The number needs to increment by 1 each visit and be absolutely 99.99% accurate.

---

### Post by SeijiSensei on 2011-09-23
> **ki4jgt said:**
> I need to be able to keep a single (changing) variable with traffic that varies from 4 - 1000 users per minute. The number needs to increment by 1 each visit and be absolutely 99.99% accurate.

Just count log entries then in /var/log/apache2/access.log.

---

