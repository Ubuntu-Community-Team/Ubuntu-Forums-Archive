---
title: "Storing Data in Java"
date: 2009-01-21
forum: Programming Talk
---

### Post by Sub101 on 2009-01-21
Hi, What I would like to know is if there is a method to store data in java once you have closed the application. 

  For example, if my application were a shopping list. Once I have entered the data how can I save the items so they are still available once I have closed and reopened the application. I am familiar with arraylists etc but in my experience they do not hold the data when the application is closed. I am also aware of writing to a text file but feel better methods must be available.

Thanks for your time.

---

### Post by CptPicard on 2009-01-21
See "serialization". An alternative is writing your own binary format, or perhaps using some kind of database.

---

### Post by DocForbin on 2009-01-21
For your example with a shopping cart, typically you would store the cart contents in a database.

More generally, for persistent objects, google java hibernate.

---

### Post by cl333r on 2009-01-22
> I would like to know is if there is a method to store data in java once you have closed the application.
There isn't just a method, there's a whole wealth of history, possibilities, APIs and implementations behind it. As DocForbin noted google for hibernate, or JPA or EclipseLink or grab a (good, > 2005) Java book.

[http://java.sun.com/docs/books/tutorial/jdbc/index.html](http://java.sun.com/docs/books/tutorial/jdbc/index.html)

---

### Post by jespdj on 2009-01-22
> **CptPicard said:**
> See "serialization". An alternative is writing your own binary format, or perhaps using some kind of database.
Serialization is easy, but it is not a good choice for long-term storage of Java objects. Because when you modify your source code, the old serialized files might not work anymore (since they represent old instances of the classes).

I'd advise you to start with a simple database and JDBC; cl333r posted a link to the JDBC tutorial above.

---

### Post by CptPicard on 2009-01-22
> **jespdj said:**
> Serialization is easy, but it is not a good choice for long-term storage of Java objects.

Very true. But this guy appears to be quite a beginner so starting with the easiest way out may not be out of the question... at least Hibernate/JPA stuff sounds overkill.

But yes, in the database case, raw JDBC would probably be the way to go.

---

### Post by Sub101 on 2009-01-22
Thanks for all the info from everyone. Serialization looks like a good starting point on the topic for me and I would rather use that than mess around with SQL. 

 Thanks for all the advice.

---

### Post by DocForbin on 2009-01-22
You could also use xml.

or json

fwiw, embedded databases like derby and sqlite are easy and lightweight

---

### Post by Reiger on 2009-01-22
Depending on the app type you may just want to use a plain text format? Say shopping lists (or recipes): these need not statisfy complex requirements ensuring data integrity, and in the case of shopping list all you ever really need is just a plain text file with rows of items to buy anyway...

---

### Post by eye208 on 2009-01-22
Check out

java.beans.XMLEncoder
java.beans.XMLDecoder

for serialization to XML files. It's very easy and immune to implementation changes.

---

