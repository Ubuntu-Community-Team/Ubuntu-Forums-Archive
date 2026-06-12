---
title: "[Python] sql or text files"
date: 2012-04-01
forum: Programming Talk
---

### Post by ki4jgt on 2012-04-01
For a server which stores information (with thousands of entries) which would be a better method of storing and accessing said information:

Text files
sql

---

### Post by hakermania on 2012-04-01
AFAIK, databases are exactly for this purpose, so I would suggest sql !

---

### Post by codemaniac on 2012-04-01
If you need to deal with "thousands of entries" ,you can use some loader utilities like Sqlloader(oracle) that can load your raw data(in csv/txt file) to the database and use Python extension modules that allows access to databases .

---

### Post by codemaniac on 2012-04-01
Here is a link to get you started .

[http://www.oracle.com/technetwork/articles/dsl/python-091105.html](http://www.oracle.com/technetwork/articles/dsl/python-091105.html)

---

### Post by Some Penguin on 2012-04-01
Text files?  Not in an individual text file, but a filesystem-based store isn't necessarily insane.

You've basically asked an unanswerable question since you've said absolutely nothing about access patterns or what you're storing, just that you're working with a trivial amount of data.  For all we know, you might be better off with a simple key-value store rather than a full relational database.

---

### Post by Ropes on 2012-04-02
If your database isn't going to get that large, you said only thousands; Python's Sqlite3 library might be a simple choice.  It's simple because it doesn't depend on any external servers/services, all you have is write normal sql and it dumps to a file.

---

### Post by ki4jgt on 2012-04-02
> **Some Penguin said:**
> Text files?  Not in an individual text file, but a filesystem-based store isn't necessarily insane.

You've basically asked an unanswerable question since you've said absolutely nothing about access patterns or what you're storing, just that you're working with a trivial amount of data.  For all we know, you might be better off with a simple key-value store rather than a full relational database.

I'm a little skiddish about sharing the project. It's not mine to share but

Basically what I need stored is two things

signing authority
Ownership certificates

I need the signing authority to store gpg keys of approved individauls who may sub-authorize people into the system. Each of these gpg keys will be signed by a master key.

In the Ownership Certificates, I need the sub-authorized individuals to have a document which basically tells the computer how to connect to them (IP address, IM, other contact information). Once the certificate has been signed by someone in the Signing Authority, it becomes official and the individual may use their own personal key to update contact information.

If this makes any sense at all.

---

### Post by CynicRus on 2012-04-02
In my opinion, the most efficient way to store data for authorization, and any keys - a sql database. In addition, a sufficiently large number of entries. BUT - if you want to use the same file, but do not use the sql - I would have kept the records in a serialized binary file, which would also encrypted with it.

---

