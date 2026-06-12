---
title: "SQLite 3 query problem"
date: 2010-03-14
forum: Programming Talk
---

### Post by Shippou on 2010-03-14
Hello all.

Is this an SQLite bug?

We have a form that asks a password. PHP "encrypts" it using its SHA1 function. Then we send the query to a database, which then authenticates if the password is correct. But then, it seems that SQLite 3 truncates string queries.

For example, the database has the following account in it:

username: foobar
password: ada2146efc57d87ef0388b305cc7a1406fcff5f2

The following query returns null, even though it matches the one in the database:

SELECT * FROM Accounts A WHERE A.username='foobar' AND A.AdminPassword='ada2146efc57d87ef0388b305cc7a1406fcff5f2'

Even SQLiteStudio returns null, and also the command-line SQLite.

Can someone help me regarding this problem?

Thanks in advance.

Shippou

---

### Post by Shippou on 2010-03-14
Just bumping up this post. I really need help. Sorry for being persistent.

---

### Post by heikaman on 2010-03-14
> **Shippou said:**
> 
SELECT * FROM Accounts A WHERE A.username='foobar' AND A.AdminPassword='ada2146efc57d87ef0388b305cc7a1406fcff5f2'

Is there a space in your query ?

---

### Post by Shippou on 2010-03-14
> **heikaman said:**
> Is there a space in your query ?

My GOSH, you're right! 

I really didn't notice that one. Maybe because of frustration. :)

I am SO thankful.

I tested it (the corrected query) in SQLite, and it works right now (though the query returns only 16 characters in the password field, but then it works).

Thank you very much.

I would still test this thoroughly, though. Maybe I'll uncover something. :)

---

