---
title: "looking for small database engine with API for C"
date: 2006-06-26
forum: Programming Talk
---

### Post by tomcio on 2006-06-26
Hi!

Generally I found good database for me - SQLite, but I doesn't have one , very important feature, SQL isn't fully implemented, query "ALTER TABLE" is not supported. SQLite is ideal for me, but I need to have support for "ALTER TABLE" :( 

I was looking for other database engine, but I didn't find nothing interesting, so I hope, that you will help me. Here are some things, which database engine must have:
- support Linux and Windows systems
- have API for C language
- need to be small, like SQLite, without support for users, extended security functions, only base and simple data keeping
- it should create database file (or files) under the given path
- it must support SQL92 better then SQLite

Any ideas? ;)

---

### Post by Daverz on 2006-06-26
You could try embedded mysql or firebird, but they aren't anywhere near as compact as sqlite.

---

### Post by tomcio on 2006-06-26
Yes, that's the reason why i don't want to use them, they are to big for me :( 

other ideas?

---

### Post by Daverz on 2006-06-27
Learn to live without alter table?  Write a script that dumps your table data, makes your schema change, and loads your data back.

---

### Post by tomcio on 2006-06-27
Yes, I think, that's is the only way to do it. Maybe it won't look too good, but it will work ;) 

thx!

topic can be closed, with conclusion, that SQLite is the best solution for problems simillar to my.

---

### Post by mariuz on 2008-11-21
> **tomcio said:**
> Yes, that's the reason why i don't want to use them, they are to big for me :( 

other ideas?

they are not so big if you compare them with oracle or db2 installers 

for example the firebird classic package has something like 4M
[http://packages.ubuntu.com/jaunty/firebird2.1-classic](http://packages.ubuntu.com/jaunty/firebird2.1-classic)
and i think it could be stripped of docs and tools if you need it for embedded usage
also there is the embedded version that could be used

[http://www.firebirdfaq.org/Firebird-Embedded-Linux-HOWTO.html](http://www.firebirdfaq.org/Firebird-Embedded-Linux-HOWTO.html)

---

### Post by stevescripts on 2008-11-21
Yes, SQLite's ALTER TABLE is a bit constraining

[http://www.sqlite.org/lang_altertable.html]("http://www.sqlite.org/lang_altertable.html")

That said, +1 on what was posted by Daverz.

Steve

---

