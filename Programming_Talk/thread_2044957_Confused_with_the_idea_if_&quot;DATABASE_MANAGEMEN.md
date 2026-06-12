---
title: "Confused with the idea if &quot;DATABASE MANAGEMENT SYSTEM&quot;"
date: 2012-08-20
forum: Programming Talk
---

### Post by vikkyhacks on 2012-08-20
I recently started to learn about DBMS but I found many terms likes 
   1. RBDMS
   2. DBMS
   3. OODBMS
   4. XML Databases
   5. NoSQL  
                   kinda stuff and so ....
so what are these ???? Are they types of databases or what ??? 

if they are the types of databases then what are these 
    [http://www.personal.psu.edu/glh10/ist110/topic/topic07/topic07_06.html]("http://www.personal.psu.edu/glh10/ist110/topic/topic07/topic07_06.html")

I am learning these concepts on my own and I am a beginner with database concepts ... please I need help !!!

---

### Post by lykwydchykyn on 2012-08-20
A "database management system" is just a generic term for database software.  The other terms just get more specific about exactly how the data is organized, stored, and accessed.

The most common kind that people think of is "relational".

---

### Post by trent.josephsen on 2012-08-20
Loosely speaking, a **database** is just something you can store data in. A simple example of a database might be a file containing a list of contact names and phone numbers. It doesn't have to be complicated, it just has to store data.

```
# name, telephone number
Edgar Allan Poe, 555-3234
Emily Dickinson, 555-5666
Nathaniel Hawthorne, 555-9123
```

That works pretty well if all you need is to look up the phone numbers of your contacts. You could use simple tools like grep and sed, or just a text editor, to look up people or edit their names and numbers. But suppose you had a thousand people in this file and you wanted to keep it sorted alphabetically by last name. You might write little programs to add and delete entries, to automate a lot of otherwise tedious work.

```
$ ./addcontact 'Mary Shelley' '555-2879'
$ ./delcontact 'Emily Dickinson'
$ ./findcontact 'Hawthorne'
Nathaniel Hawthorne's phone number is 555-9123
```

*Voila*, you've just created a **database management system** or DBMS. A DBMS is just a software package that interfaces with a database.

Now this is obviously not what you might call a *general purpose* DBMS; it's only capable of storing one "table" with two "fields", and it will most likely suffer performance issues when your contacts list gets very large. So let's add a few features, like the ability to create and edit distinct "tables":
```
$ ./mktable prices 'item name' 'cost'
$ ./addto prices 'Large Pepperoni Pizza' '$19.99'
```
which might create a file that looks like this:
```
# item name, cost
Large Pepperoni Pizza, $19.99
```

and for some added convenience, let's merge these little programs into one big one that acts kind of like a shell for our database, interpreting a special language created for it, so we could do the previous example like this:

```
> CREATE TABLE NAMED 'prices' WITH FIELDS 'item' AND 'cost'
> ADD TO TABLE 'prices' item='Large Pepperoni Pizza', cost='$19.99'
```
Oh. Huh. You know, this is beginning to look a lot like SQL.

The defining feature of a **relational database** is the ability to relate data in one part of the database to data somewhere else. For instance, I might have a table of contacts, and a table of cars, and I could relate them by saying "This contact owns/drives this kind of car". How that relation is implemented is up to you.

**Object-oriented databases** store data as objects rather than as rows in tables. In some ways this is self-explanatory but I always feel it's a cop-out answer. All the same, I can't really think of a better way to describe object databases, especially as many databases that are accessed with an object model are in fact relational under the surface.

It's important not to get confused between the different database *formats*, like the flat file we originally created, and different *database management systems*, like SQLite or Postgres. Different formats may excel at storing different types of data, but the DBMS you use is the final arbiter of what kind of data you can store and what you can do with it.

Clear as mud?

---

### Post by vikkyhacks on 2012-08-20
Many thanks for this clear explanation, I can now understand what a database is but what about the rest ???
what are XML Databases, NoSQL and I recently found out that there are not just OODBMS but also ODBMS ... I am clear with databases but what do these knda stuff have to do with DATABASE MANAGEMENT SYSTEM

---

### Post by trent.josephsen on 2012-08-20
OO, relational, and NoSQL are more or less just different ways of *modeling* a "real" database so that you can more easily use it. Like C, Java and Perl have different ways of modeling a "real" computer so that you can more easily write programs for it.

(Before somebody tries to correct me) I'm oversimplifying. There are real differences between "real" databases, but the bottom line is that a database stores data, and whether it's a flat text file, a complex array of binary blobs, or an encrypted .mp3 on the ISS makes no substantative difference as long as you can use a DBMS (which is a software interface to a database) to interface with it.

Don't worry too much about all the different ways you can interface with a database just now. You don't need to know all of them to get a better understanding of databases. My advice is to install SQLite if it's not already available, and try to implement a simple contact list, or track your music collection or something like that. If you have some money to put toward this cause, [Head First SQL](http://www.headfirstlabs.com/books/hfsql/) would be a good place to start; it's quite practical and not too overwhelming.

---

