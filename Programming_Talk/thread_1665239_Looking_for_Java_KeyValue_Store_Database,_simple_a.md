---
title: "Looking for Java Key/Value Store Database, simple as possible"
date: 2011-01-12
forum: Programming Talk
---

### Post by SNYP40A1 on 2011-01-12
I am looking for a free open-source database.  I need key-value store and plan to program in Java.  Basically, a persistent HashMap is what I'm looking for.  I would like to access the database with multiple readers (no writers) concurrently, but that's not a hard requirement yet.  I have looked at Berkley DB Java edition, looks good, but pretty complicated.  Also looked at Tokyo Cabinet, excellent performance, Java API, but it can only store arrays of bytes and strings...if Tokyo Cabinet could simply accept objects, then casting to the required subclass would be simple.  However, having to encode / decode very Java object that I plan to store (arrays of objects) would really kill performance.  Although I like the simplicity of Tokyo Cabinet and since I don't plan to store an enormous amount of data, maybe an array of 20000 objects (each object holds 3 integers, 2 doubles) at the longest, it could work, but does anyone know of a better database for my situation?  I'd like to be able to iterate through the keys in the database, but no need for SQL or query language.

---

### Post by MadCow108 on 2011-01-12
what you want is a nosql database, there are many
I cannot tell you which one is best for your requirements but here is huge list of possibilities:
[http://nosql-database.org/](http://nosql-database.org/)

---

### Post by Some Penguin on 2011-01-12
> **SNYP40A1 said:**
> However, having to encode / decode very Java object that I plan to store (arrays of objects) would really kill performance.

Unless you're storing a full byte-for-byte snapshot of the entire process space, how do you expect to store objects without encoding / decoding them?

---

### Post by SNYP40A1 on 2011-01-12
> **Some Penguin said:**
> Unless you're storing a full byte-for-byte snapshot of the entire process space, how do you expect to store objects without encoding / decoding them?

Berkeley DB does it, but you have to create a view that is associated with a specific class for each object that you plan to store.  However, an object does have some information about what it is.  That's how casting works.  An object inspects itself to see if it's of the casted type.  If not, it returns null.  The object doesn't know the exact class name though.  I suspect that if you created two classes as:

class A
{
   private int num;

   public int getNum() { return num; }
}

class B
{
   private int numa;

   public int getNum() { return numa; }
}

that class A can cast as class B, class B can cast as class A.  I haven't tried that though, just speculating...

Anyways, I have seen the nosql website.  If anyone knows of a better solution for my needs described here than Berkeley DB, let me know.

---

### Post by Some Penguin on 2011-01-12
So in other words, it's still encoding and decoding objects.

---

### Post by Reiger on 2011-01-12
Database is overkill, simple file will do.

---

### Post by Some Penguin on 2011-01-12
But TokyoCabinet, DBM, et al will provide much faster access than a flat file.

TC isn't hard to use, and paired with a lightweight serialization method will be plenty fast.  If you care about supporting versioning et al, you can use something lightweight and extensible like JSON (codehaus/Jackson library is pretty clear); if you don't, you can take advantage of the fact that Java doesn't really have endianness or type size problems because they're fully specified, so you can just read/write bytes if you prefer.

---

### Post by SNYP40A1 on 2011-01-13
> **Some Penguin said:**
> So in other words, it's still encoding and decoding objects.

Humm...yes, you're right.  The difference is that Berkley DB handles the encode / decode whereas with Tokyo Cabinet, user has to do that part.

---

