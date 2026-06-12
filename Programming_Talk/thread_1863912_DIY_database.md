---
title: "DIY database?"
date: 2011-10-18
forum: Programming Talk
---

### Post by TheHimself on 2011-10-18
I would like to have database capabilities in my programs but am not willing to use sqlite (blame the learning curve). Working with home-made databases whose columns have fixed length is easy however I don't know how to manage variable-length columns (for example the path to files in a database of files).  If you want to modify such an entry don't you have to rewrite all the database contents following it? :(

A similar problem is erasing a record from a database. I do this by putting a null '\0' at the beginning of the line corresponding to the record.

---

### Post by karlson on 2011-10-18
> **TheHimself said:**
> I would like to have database capabilities in my programs but am not willing to use sqlite (blame the learning curve). Working with home-made databases whose columns have fixed length is easy however I don't know how to manage variable-length columns (for example the path to files in a database of files).  If you want to modify such an entry don't you have to rewrite all the database contents following it? :(

A similar problem is erasing a record from a database. I do this by putting a null '\0' at the beginning of the line corresponding to the record.

Have you considered BerkeleyDB if you want to embed DB into your application?

---

### Post by moldaviax on 2011-10-18
could you use a csv file so that you could pick out variable length items between commas?

eg assuming you are using files, something like this...

Id, FileType, FilePath
1, jpg,/home/picture/pic.jpg
2, odf,/home/docs/doc.odf

so you can parse out the id, file type and path - in java easy to achieve with a StringTokenizer

M.

---

### Post by gsmanners on 2011-10-18
Easiest thing in the world:

[http://docs.python.org/library/pickle.html](http://docs.python.org/library/pickle.html)

---

### Post by TheHimself on 2011-10-19
> **moldaviax said:**
> could you use a csv file so that you could pick out variable length items between commas?

eg assuming you are using files, something like this...

Id, FileType, FilePath
1, jpg,/home/picture/pic.jpg
2, odf,/home/docs/doc.odf

so you can parse out the id, file type and path - in java easy to achieve with a StringTokenizer

M.

Yes, of course. But what if you needed to modify one of those variable-length entries in the middle of the database? Does one have to rewrite the whole database file? 
(There is a similar problem when editing in the middle of a text file. I don't know how text editors handle this. I guess for a small text file one can easily rewrite the whole file but for a huge database that may not be the best option.)

---

### Post by moldaviax on 2011-10-19
Personally I would persist with SQLLite or  [http://www.oracle.com/technetwork/java/javadb/overview/index.html](http://www.oracle.com/technetwork/java/javadb/overview/index.html)

or use XML+XPATH :-) 

However I think [http://download.oracle.com/javase/tutorial/essential/io/rafs.html](http://download.oracle.com/javase/tutorial/essential/io/rafs.html) describes a java object (random access file) that might be of help if you want to build something from scratch. That does assume you are using Java...

M.

---

