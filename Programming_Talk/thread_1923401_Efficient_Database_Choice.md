---
title: "Efficient Database Choice"
date: 2012-02-10
forum: Programming Talk
---

### Post by Magnificence on 2012-02-10
Hello fellow Ubuntu users,

I'm developing an application (if you can call it that), and it needs a database. I'm wondering what would be the most efficient type of database to use? Resources are pooled so I don't worry about implementations that pool the databases' resources. Also, you can expect a lot of entries, so I'm looking for an implementation that doesn't make look-up requests expensive.

So I've experimented with an SQL database, but I have a feeling it is not as fast as working with files.

My current implementation uses a file for each entry, with it's filename as identifier. I would think that adding, removing and looking up files would be pretty quick, but could somebody verify this? The only problem I've found for this implementation is that  most files will usually be only a few bytes, and each files will take up a multiple of 4 KiB of space, so it'll use far more space than it actually needs.

All help is appreciated!

---

### Post by ibrahimtawbe on 2012-02-10
for database now i'm using mongodb , but there are cases where it's not the best option 
have a look at [http://www.mongodb.org/](http://www.mongodb.org/)

---

### Post by Rafterman414 on 2012-02-10
Apache Derby makes for a pretty good embedded database for Java applications if that is what you are going for, but it is best suited for single connections to the db, it can be configured to allow for multiple connections but I am not sure how well it functions like that.

---

### Post by JDShu on 2012-02-10
Facebook runs on MySQL, probably one of the least scalable relational databases. I suspect that you don't have a good reason to use a NoSQL or other performance improving techniques.

---

### Post by llanitedave on 2012-02-10
If the database is embedded into your application and doesn't have a lot of simultaneous users, I'm not sure how you can beat sqlite.

---

