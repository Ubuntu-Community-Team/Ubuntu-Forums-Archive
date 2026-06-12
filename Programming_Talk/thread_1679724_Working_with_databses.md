---
title: "Working with databses"
date: 2011-02-01
forum: Programming Talk
---

### Post by amuh on 2011-02-01
Iv'e been programming on and off for a while, mostly Java. And Iv'e been thinking about how to preferably work with databases. Iv'e been told that it's a good idea of making objects out of the data in the database. For example;
A table called 'car' contains some basic information about cars, such as 'color', 'brand', 'horsepower' '...'. And in Java i've written a car-class with the same attributes and used that object instead of connecting to the database. 
But now iv'e been tinkering with an app which would require constant connection to the database. And thus, perhaps, i don't need to read data from the database into objects? Instead just make (alot of) select-querys and print the data on screen?

Whats the actual benefits of store data inside objects (or arrays, etc), when its so easy and quick to fetch the data over and over again with databases?

---

### Post by fct on 2011-02-01
Hmmmm, you should research object persistence:

[http://en.wikipedia.org/wiki/Java_Persistence_API](http://en.wikipedia.org/wiki/Java_Persistence_API)

Basically with beans DB updates are automatic and pooled depending on the changes to object instances.

JBoss Hibernate is one good implementation.

---

### Post by amuh on 2011-02-01
Ok! Thanks for the tip! I'll definently look into that!

---

