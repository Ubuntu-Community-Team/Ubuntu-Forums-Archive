---
title: "mysql persistence"
date: 2007-02-22
forum: Programming Talk
---

### Post by derby007 on 2007-02-22
Could anyone recommend a good way to do Java DB PERSISTENCE ? ie. i have a GUI frontend that gets data from user (or visa-versa) & i have a MySQL database. It will be a one user system, so its fairly straight foreward, no web based activity, yet !! Should i be looking at ONE Class doing the Java SQL statements or should i be looking at some kind of Java Pattern, ie. Factory or Facade etc., or creating Classes that represent the Tables in the DB ? 
  ie. I'm just looking for ideas on a best/straight-foreward approach... :) 

  So far i have my Java GUI talking to a Java Class that writes/reads from the DB using MySQL statements.

---

### Post by kidders on 2007-02-22
Hi there,

I've tried both approaches to this in the past. Which one to choose from really depends on what the eventual purpose of your app will be, what kinds of database operations you want to be able to perform easily, and how extensible you want your work to be.

Having said that, I would try to stick to a simple (less elegant) solution if possible ... Java is inefficient enough, without adding more layers of overhead unnecessarily!

---

### Post by derby007 on 2007-02-23
yeah, i'll keep it simple for now, at the mo my GUI is sending messages to a static persistence class that talks to the database. i was looking into patterns ie. for when i add more functionality, like more windows, more inserts, updates, deletes....any ideas / examples on patterns for me?

---

### Post by kidders on 2007-02-23
> **derby007 said:**
> any ideas / examples on patterns for me?What is your app going to do?

I once went completely loopy and decided that I wanted the database underlying my app to be in *total* control of the Java class structure. My application automatically constructed classes based around database tables, with fields and methods that reflected the columns in them. I was trying to engineer a scenario where, if I created a table called "Customer", say, I could proceed immediately to **Customer c = new Customer();** (to set about inserting a new row in the Customer table), or **Customer c = Customer.getCustomer(12345);** (to instantiate a row from the table).

By defining a series of naming conventions, I was able to set up rudimentary relationships between tables, that would then allow me to write **Invoice[] arr = c.getInvoices();** which would eventually be translated into something like **SELECT * FROM invoice WHERE customerid=12345** ... or go backwards, with **Customer c=invoice.getCustomer();**.

At the time, I thought getting the Java to (almost) write itself was a neat trick ... but talk about overcomplicating things!!

Something less ridiculous you could try would be to write yourself a few classes to reflect the basic structures of a database (as you suggested). If you had Connection, Database, Table, Row & Field classes, for example, you could write something like this...

```
Connection con=new Connection("localhost", "user", "pass");
Database d=con.getDatabase("whatever");
Table[] tables=d.getTables();

for (int i=0;i<tables.length;i++) {
	// Put the table names into a menu, or something
}
```

You could perhaps dynamically construct JPanels for use in entering/editing the contents of a table row, by asking your Table class for structural information, and so on.

Is that anything like what you were asking about? The trouble is, you see, that Java->MySQL interfaces like these, that model basic MySQL concepts, already exist.

---

### Post by derby007 on 2007-02-23
Thanks for the info. I am setting up a system whereby a user will be interacting with a GUI to enter, update, delete, gather info from a DB. I was messing around with ResultSets & ResultSetMetaDatas. I've only made a start into it, so i haven't had a need to Instantiate classes yet! I'm trying to get my head around this WHOLE  (Java-MySQL-Persistence-GUI) idea.
Any other tips for me, the Table one is good, but i don't have : DATABASE,
	Database d=con.getDatabase("whatever");
this is not part of my 'java.sql.*' ?? or am i missing something....are you using some other Library?  Would it be DatabaseMetaData?

---

### Post by kidders on 2007-02-23
> **derby007 said:**
> i don't have : DATABASE,
	Database d=con.getDatabase("whatever");
this is not part of my 'java.sql.*' ?? or am i missing somethingI just made those class names up ... you see, I assumed you'd probably be wrapping the Java SQL stuff in classes of your own, to make them less irritating to use. Calling them "Connection", "Database" and "Table" just seemed sensible.

The other advantage to that approach is that any code that sits on top of your wrappers would be platform-independent. You could switch between MySQL libraries ... or even move to Oracle ... without having to rewrite anything but the wrappers.

---

### Post by derby007 on 2007-02-23
Cheers, maybe i should have read your post with more intelligence, i just read toooo quickly at times.......or maybe thats my excuse for little intelligence.
>> trouble is, you see, that Java->MySQL interfaces like these, that model basic MySQL concepts, already exist.>>
    Can u point me in this direction........links, etc.  :)

---

### Post by kidders on 2007-02-24
> **derby007 said:**
> Can u point me in this directionGoogle is your best bet ... what's available has changed a lot since I last needed to do this sort of thing.

---

### Post by lloyd mcclendon on 2007-02-25
hibernate may not be necessary for this but it is the best persistence service out there.  it sounds to me like you realize this is the direction you know you should go, transparent persistence of objects.  save(aVeryComplicatedObjectGraph) .. a complex web of tables, have fun writing & maintaining a sql statemnt.

it's has a lot of necessary but usually rare features: lazy loading, caching, a so-so query language, decent (but not perfect yet) generics & collections support.   it is not easy to get moving with though, you pretty much will have to use spring to get the infrastructure for it well setup. this is still 100x easier than dealing with the low level crap of jdbc, writing those crazy sql statments, binding in and out your parameters.  you should see some of the sql hibernate has generated for me, i could never type something like that!

after you understand it well enough, it can almost completly abstract the database from you.  a big part of understanding it is knowing what it won't do, you're still stuck with transaction & session management.  spring can help a great deal with this crap.

i would say if you don't really have a deadline on this, and have some time to screw around and learn something that is flat out useful and very academic check it out.  it is pretty fun.  i'm getting very close to an ivory tower of data access service.  well actually there's still a lot to do, but once i can figure out collections of collections, there's not too much i can't persist and pull out with a single line of code.  or i could just scrap the whole thing and write 100 lines of unworkable sql.

---

### Post by daneel_olivaw on 2007-02-25
martin flowler's book is the best book talking about java data persistence - the title is "Patterns of Enterprise Application Architecture", [this]("http://www.martinfowler.com/") is his link on web

some core patterns about that can be found online at [this]("http://java.sun.com/blueprints/corej2eepatterns/Patterns/") link; the most important is DAO - data access object, and then comes the DTO, data transfer object.. take a read at them

in a few words, if u have the One class in ur system, u will have:

OneDao - the class that talks to the DB and stores / retrieves / updates / delets tuples from the one table in which the One entity resides

OneDto (or simply One) - the class which carries domain information about the one entity and that OneDao will give to whoever requests to have contact with the One entity

another class which is responsible to implement this basic workflow:

1. receive clients requests
2. instruct the Dao to do something on the DB to satisfy them
3. receive the Dto from the Dao and give it back to the client for it to manipulate it

in the last link i gave you, the pattern which basically does this is called Business Object.

PS: there are big massive implementations of all of this.. i mention a couple, in order of dimensions and complexity: Hibernate and Ejb, but i suggest you try to code something simple yourself first, and then eventually choose something at your need.

---

### Post by cybrid on 2007-02-25
Just one word, HIBERNATE

---

