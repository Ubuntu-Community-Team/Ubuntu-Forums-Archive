---
title: "[Python] What database type should I use?"
date: 2011-06-29
forum: Programming Talk
---

### Post by ki4jgt on 2011-06-29
I want to have the capacity to handle thousands of users. All I want to do however is simply keep the user's name, password, and their score. No personal information about them whatsoever. Any suggestions on what type of database I should look into? The server has already been setup.

---

### Post by trizrK on 2011-06-29
> **ki4jgt said:**
> I want to have the capacity to handle thousands of users. All I want to do however is simply keep the user's name, password, and their score. No personal information about them whatsoever. Any suggestions on what type of database I should look into? The server has already been setup.
Try an Oracle solution.

---

### Post by juancarlospaco on 2011-06-29
DB for what ?
If its a Web based thing, i may suggest using OpenID for users password, 
Like this forum, and a MySQL to keep the score part only.

---

### Post by ki4jgt on 2011-06-29
> **juancarlospaco said:**
> DB for what ?
If its a Web based thing, i may suggest using OpenID for users password, 
Like this forum, and a MySQL to keep the score part only.

The clients are not html based. They're extremely text based.

---

### Post by llanitedave on 2011-06-29
What kind of server arrangement are you looking at?  If it's a game server with lots of participants, either MySQL or Postgresql are your best bets.

---

### Post by b@sh_n3rd on 2011-06-29
I'd say go for PostgreSQL, as that's what I've got experience with (with Python 3). It's pretty easy to setup and flexible, etc...but you could also go for MySQL...

---

### Post by Petrolea on 2011-06-29
I'd say MySQL, I only have good experience with it. For an offline DB, check out SQLite.

---

### Post by TwoEars on 2011-06-29
SQLite is what you want to be looking at.
[http://docs.python.org/library/sqlite3.html](http://docs.python.org/library/sqlite3.html)
Since you don't need it to be multithreaded, it will be fine for your needs. I don't suggest looking into the other databases mentioned; they are too big and pointless for your project.

---

