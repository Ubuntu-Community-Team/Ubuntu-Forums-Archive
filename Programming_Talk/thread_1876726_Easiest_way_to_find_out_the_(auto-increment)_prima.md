---
title: "Easiest way to find out the (auto-increment) primary key for an entry in a MySQL db"
date: 2011-11-06
forum: Programming Talk
---

### Post by Mezzoforte on 2011-11-06
I'm pretty new to MySQL and PHP, and the other day I stumbled over the problem of how to determine the ID of an entry in a database. I'll describe the issue a little more clearly.

I have a database with an ID column and some other columns. The ID column is the primary key and is set to auto-incremental. Let's say we're submitting some simple data that consists of a title and some content. So, there is one title column and one content column in the database (in addition to the ID column). If I submit a title and some content to the database (using a form on a website and PHP to send the queries), I want to know the ID that the submitted data is associated with.

I started out using a simple method, just sending another query that returned the ID column of all rows that matched the title I submitted. This becomes problematic, because there could be several equal titles in the database, and then this method can't give me a unique ID.

Is there any easy way to do this, or should I rather redesign my database? I was thinking that maybe there is a good way to find out what ID the last row in the database is, but then I thought, if there are a lot of simultaneous queries made to the db there might be a risk that the database has been changed by another user before we know which ID the first user's submitted row was assigned.

Any ideas?

---

### Post by TheOrangePeanut on 2011-11-06
It's easier than you think.  Take a look at this function.

[http://php.net/manual/en/function.mysql-insert-id.php](http://php.net/manual/en/function.mysql-insert-id.php)

---

### Post by Mezzoforte on 2011-11-07
Thanks, exactly what I was looking for, and simple too! :)

---

